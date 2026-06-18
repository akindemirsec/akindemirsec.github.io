---
layout: post
title: "MemLabs Lab 1 - The Black Window"
date: 2024-01-12
categories: [forensics, ctf]
tags: [volatility, memory-forensics, ctf-writeup, memlabs]
excerpt: "MemLabs Lab 1 walkthrough - recovering files from a crashed system using console output decoding, mspaint memory extraction, and RAR archive cracking."
---

## Challenge Description

My sister's computer crashed. We were very fortunate to recover this memory dump. Your job is get all her important files from the system. From what we remember, we suddenly saw a black window pop up with some thing being executed. When the crash happened, she was trying to draw something. Thats all we remember from the time of crash.

---

## Solution

### Stage 1: Console Output

First get the image info:

![imageinfo](/assets/images/blog/Pasted%20image%2020240112133345.png)

Scan the console outputs:

![consoles](/assets/images/blog/Pasted%20image%2020240112134019.png)

As you can see there is an encoded text, when you decode the text it gives us the first flag:

![decoded flag 1](/assets/images/blog/Pasted%20image%2020240112134123.png)

### Stage 2: MSPaint Memory

For the second stage I extracted memory page of mspaint.exe process:

![memdump mspaint](/assets/images/blog/Pasted%20image%2020240112134217.png)

Then I opened the extracted file with GIMP and it gives me the second flag: **`flag{G00d_Boy_good_girL}`**

### Stage 3: The RAR Archive

For the last stage, I started to investigate what the user did in Winrar. And it seems that the user opened a file called Important.rar:

![filescan winrar](/assets/images/blog/Pasted%20image%2020240112135351.png)

I use filescan command to find Important.rar then I dumped it with dumpfiles command:

![dumpfiles](/assets/images/blog/Pasted%20image%2020240112135546.png)

When I tried to unrar the rar file I found that the file was password protected but a hint was left:

![password hint](/assets/images/blog/Pasted%20image%2020240112135722.png)

I used hashdump command for getting Alissa Simpson's NTLM hash and used it as the password:

![extracting RAR](/assets/images/blog/Pasted%20image%2020240112140124.png)

And this is the last flag of Lab 1:

![flag 3](/assets/images/blog/Pasted%20image%2020240112140159.png)

## Key Takeaways

- "Black window" = cmd.exe - always check console outputs
- MSPaint stores pixel data in memory that can be extracted and viewed with image editors
- NTLM hashes from hashdump can serve as passwords for encrypted archives
