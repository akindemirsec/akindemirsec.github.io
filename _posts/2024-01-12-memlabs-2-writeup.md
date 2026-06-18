---
layout: post
title: "MemLabs Lab 2 - The Environmental Activist"
date: 2024-01-12
categories: [forensics, ctf]
tags: [volatility, memory-forensics, ctf-writeup, memlabs, keepass]
excerpt: "MemLabs Lab 2 walkthrough - finding flags through environment variables, KeePass password databases, and browser history analysis."
---

## Challenge Description

One of the clients of our company, lost the access to his system due to an unknown error. He is supposedly a very popular "environmental" activist. As a part of the investigation, he told us that his go to applications are browsers, his password managers etc. We hope that you can dig into this memory dump and find his important stuff and give it back to us.

---

## Solution

### Stage 1: Environment Variables

First get the image info:

![imageinfo](/assets/images/blog/Pasted%20image%2020240112142532.png)

In the description "environmental" keyword gives us a hint so lets scan environment variables. When we scan environment variables we can see there is an encoded string `ZmxhZ3t3M2xjMG0zX1QwXyRUNGczXyFfT2ZfTDRCXzJ9`:

![envars - encoded string](/assets/images/blog/Pasted%20image%2020240112141500.png)

When we decode the string (Base64) it gives us the first flag:

![decoded flag 1](/assets/images/blog/Pasted%20image%2020240112141528.png)

### Stage 2: KeePass Password Database

User uses KeePass as password manager so we have to look for the KeePass file extension:

![keepass files](/assets/images/blog/Pasted%20image%2020240112141140.png)

Then we should search and dump the .kdbx file:

![dump kdbx](/assets/images/blog/Pasted%20image%2020240112143457.png)

Alright we dumped the file but we don't know the password yet. Let's go on investigating.

I tried to search files with .txt extension or files named password but I couldn't find anything:

![searching password](/assets/images/blog/Pasted%20image%2020240112144246.png)

Then I tried to search the "password" keyword with grep -i to ignore case and there it is - a file named Password.png:

So let's dump the file:

![dump password.png](/assets/images/blog/Pasted%20image%2020240112144632.png)

![dumped password file](/assets/images/blog/Pasted%20image%2020240112144735.png)

Good. Then I installed KeePass on my Windows 10 VM and I opened the password database. And there is the second flag:

![keepass flag](/assets/images/blog/Pasted%20image%2020240112150321.png)

### Stage 3: Browser History

In the description also "browser" is quoted so let's look at the browser history:

![browser history](/assets/images/blog/Pasted%20image%2020240112150938.png)

Dump the file:

![dump history](/assets/images/blog/Pasted%20image%2020240112151128.png)

And open it in SQLite:

![sqlite browser history](/assets/images/blog/Pasted%20image%2020240112151057.png)

When you browse history there is a Mega link. Let's check the link - there is a file named Important.zip. Try to unzip it.

This zip archive is password protected. But there is a hint:

![zip hint](/assets/images/blog/Pasted%20image%2020240112151746.png)

Encode stage 3 flag from Lab 1 with SHA and here is the password for the zip archive.

And there is the last flag in Lab 2:

![lab 2 final flag](/assets/images/blog/Pasted%20image%2020240112152638.png)

## Key Takeaways

- Keywords in quotes in challenge descriptions are usually hints (e.g., "environmental" → envars)
- KeePass databases (.kdbx) can be found in memory dumps
- Browser history files can be dumped and opened with SQLite browsers
- Flags from previous labs can be required in later challenges
