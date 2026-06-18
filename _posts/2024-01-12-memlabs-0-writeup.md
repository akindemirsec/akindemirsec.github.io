---
layout: post
title: "MemLabs Lab 0 - First Steps"
date: 2024-01-12
categories: [forensics, ctf]
tags: [volatility, memory-forensics, ctf-writeup, memlabs]
excerpt: "My walkthrough of MemLabs Lab 0 - using environment variables, XOR decoding, and NTLM hash cracking to find the flag."
---

[MemLabs](https://github.com/stuxnet999/MemLabs) is an educational set of CTF-styled challenges aimed to get people started with memory forensics. Thanks [Stuxnet999](https://github.com/stuxnet999) for creating this!

## Challenge Description

My friend John is an "environmental" activist and a humanitarian. He hated the ideology of Thanos from the Avengers: Infinity War. He sucks at programming. He used too many variables while writing any program. One day, John gave me a memory dump and asked me to find out what he was doing while he took the dump. Can you figure it out for me?

---

## Solution

First get the image info:

![imageinfo](/assets/images/blog/Pasted%20image%2020240112160738.png)

Then I use pslist command to list processes and take notes about suspicious processes.

After that I use cmdscan command to search what happened in cmd.exe. And there seen a python file executed with cmd:

![cmdscan](/assets/images/blog/Pasted%20image%2020240112160738.png)

To search what was the output I used consoles command, and there is seen an encoded text as output of executed python file. But when I tried to decode it I didn't get any normal text just random characters.

![consoles output](/assets/images/blog/Pasted%20image%2020240112160938.png)

So I tried to use envars command to scan environment variables. And there is a clue - a "Thanos" variable with "xor and password" value:

![envars - Thanos variable](/assets/images/blog/Pasted%20image%2020240112161808.png)

After decode the text with the right way in second attempt it gives us a string `1_4m_b3tt3r`. Okey this should be something but this is not the flag.

We decoded the text with XOR but we didn't see any passwords so I use hashdump command to get NTLM hashes:

![hashdump](/assets/images/blog/Pasted%20image%2020240112163357.png)

Then I used hashcat for cracking hash. Also online tools can be very useful for cracking NTLM hashes.

![hashcat result](/assets/images/blog/Pasted%20image%2020240112163506.png)

Finally when you combine these two texts the flag is:

**`flag{you_are_good_but1_4m_b3tt3r}`**

## Key Takeaways

- Environment variables can hold critical clues
- Combining multiple data sources (consoles, envars, hashdump) is essential
- Understanding encoding methods (XOR) matters in CTF challenges
