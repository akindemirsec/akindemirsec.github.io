---
layout: post
title: "MemLabs Lab 4 - The Deleted File"
date: 2024-01-14
categories: [forensics, ctf]
tags: [volatility, memory-forensics, ctf-writeup, memlabs, mft, ntfs]
excerpt: "MemLabs Lab 4 walkthrough - recovering a deleted file by exporting the NTFS Master File Table (MFT) from a memory dump."
---

## Challenge Description

My system was recently compromised. The Hacker stole a lot of information but he also deleted a very important file of mine. I have no idea on how to recover it. The only evidence we have, at this point of time is this memory dump. Please help me.

**Note:** This challenge is composed of only 1 flag.  
The flag format for this lab is: `inctf{s0me_l33t_Str1ng}`

---

## Solution

First step let's get the image info.

Then I checked processes, but I didn't see any suspicious processes except of StickyNot.exe and dllhost.exe.

After that I use cmdscan command but I didn't get anything suspicious then I use cmdline command and I get something about "dllhost.exe".

Then I used consoles command but there was nothing suspicious. After that I tried to get deeper for StickyNot.exe but there was nothing. After some failures I tried to search some files and here - there is a file named Important.txt:

![Important.txt found](/assets/images/blog/Pasted%20image%2020240114075855.png)

And let's dump it.. what? Okey - dumpfiles command can't extract the file:

![dumpfiles failed](/assets/images/blog/Pasted%20image%2020240114080143.png)

After some searches about Windows forensics I find something interesting. In NTFS (New Technology File System) there is a table named MFT - Master File Table. MFT contains information about files: where the file is, data in the file, and metadata information. I wish I had known this until today.

And the best part about this: Volatility can export MFT! (This process can take minutes)

The exported txt file was 9.5 MB and 173544 lines... Okey let's open it in a text editor and try to find something about Important.txt.

And this is what we got about Important.txt - luckily I have some experience in Malware Analysis so I'm a bit used to screens like this. This is just hexdump - you can read it easily or you can decode it.

Finally the flag is:

**`inctf{1_is_n0t_EQu4l_7o_2bUt_th1s_d0s3nt_m4ke_s3ns3}`**

## Key Takeaways

- When dumpfiles command fails, the file might be in MFT (Master File Table)
- NTFS stores small files directly in the MFT record - these can be recovered even when the file itself is "deleted"
- Volatility's `mftparser` plugin exports the entire MFT - grep through it for your target
- Reading hexdump is a useful skill for forensic analysts
