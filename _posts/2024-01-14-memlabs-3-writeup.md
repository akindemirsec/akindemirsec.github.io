---
layout: post
title: "MemLabs Lab 3 - The Evil Script"
date: 2024-01-14
categories: [forensics, ctf]
tags: [volatility, memory-forensics, ctf-writeup, memlabs, steghide, xor]
excerpt: "MemLabs Lab 3 walkthrough - decrypting XOR-encoded secrets and using steganography to recover hidden data from JPEG images."
---

## Challenge Description

A malicious script encrypted a very secret piece of information I had on my system. Can you recover the information for me please?

**Note-1:** This challenge is composed of only 1 flag. The flag split into 2 parts.  
**Note-2:** You'll need the first half of the flag to get the second.  
You will need this additional tool: `sudo apt install steghide`  
The flag format for this lab is: `inctf{s0me_l33t_Str1ng}`

---

## Solution

### Part 1: The XOR Script

First step let's get the image info:

![imageinfo](/assets/images/blog/Pasted%20image%2020240114061759.png)

Then check the processes:

![pslist](/assets/images/blog/Pasted%20image%2020240114062152.png)

I noted the processes I think suspicious:

![suspicious processes](/assets/images/blog/Pasted%20image%2020240114062237.png)

After I check cmd commands with cmdline:

![cmdline](/assets/images/blog/Pasted%20image%2020240114062747.png)

And here there are 2 suspicious commands:

![suspicious commands](/assets/images/blog/Pasted%20image%2020240114062832.png)

Let's try to extract these 2 files - evilscript.py and vip.txt:

![extract files](/assets/images/blog/Pasted%20image%2020240114063556.png)

This is the evilscript.py - as you can see this code XOR encrypts the vip.txt and encodes it with Base64.

And this is the vip.txt:

![vip.txt content](/assets/images/blog/Pasted%20image%2020240114064154.png)

After decoding it with CyberChef I got something. Key 3 is in the format of our flag:

![cyberchef decode](/assets/images/blog/Pasted%20image%2020240114064244.png)

### Part 2: Steganography

After that, in the CTF challenge it says we will need to use steghide so I am going to search for some images.

First I checked for .png file extension which is a popular image file extension, and I got a lot of files but these files are not what we're searching for:

![png search](/assets/images/blog/Pasted%20image%2020240114064921.png)

Then I checked .jpeg file extension. And here there is a file named "suspision1.jpeg". I know that this looks fake but don't forget that this is a CTF:

![jpeg search](/assets/images/blog/Pasted%20image%2020240114065309.png)

Then I extracted the file. As you can see this image looks like a random footage but in the challenge description creator said we need to use steghide:

![extracted jpeg](/assets/images/blog/Pasted%20image%2020240114065634.png)

When we try to extract file with steghide we see there is a passphrase. While doing some bruteforce tries, I checked the description again and saw: "Note-2: You'll need the first half of the flag to get the second."

![steghide passphrase](/assets/images/blog/Pasted%20image%2020240114070428.png)

The passphrase is the first part of the flag: `inctf{0n3_h4lf`

We extracted the file, and there it is - the second part of the flag.

**Final flag: `inctf{0n3_h4lf_1s_n0t_3n0ugh}`**

## Key Takeaways

- Python scripts found in memory can reveal encryption methods used
- CyberChef is great for chaining multiple decode operations (XOR + Base64)
- Steganography tools like steghide can hide data inside JPEG images
- Challenge descriptions contain critical hints - always read them carefully
