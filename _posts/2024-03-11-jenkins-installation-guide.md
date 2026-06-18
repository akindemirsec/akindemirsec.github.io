---
layout: post
title: "How to Install Jenkins on Linux"
date: 2024-03-11
categories: [devsecops, devops]
tags: [jenkins, linux, ci-cd, devops]
excerpt: "Step-by-step Jenkins installation on Debian/Ubuntu with screenshots from initial setup to the dashboard."
---

## Installation

Add the Jenkins repository and install:

```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

## Access the Web Interface

After installation, Jenkins works on `localhost:8080`:

![Jenkins login](/assets/images/blog/Pasted%20image%2020240311001957.png)

You can use cat command or a text editor to see the admin password (directory can change depending on your installation method):

![Admin password](/assets/images/blog/Pasted%20image%2020240311002350.png)

## Initial Setup

After you log in and install plugins you can create admin user:

![Create admin user](/assets/images/blog/Pasted%20image%2020240311004103.png)

After you fill in the form, you can change port and URL of your Jenkins instance:

![Configure URL](/assets/images/blog/Pasted%20image%2020240311004242.png)

And here we successfully installed Jenkins:

![Jenkins dashboard](/assets/images/blog/Pasted%20image%2020240311004411.png)

## Changing the Port

Jenkins starts on port 8080 by default. You can change the port in the web interface but sometimes you need to start Jenkins from a different port. To do this, go to the Jenkins directory `/opt/jenkins/` or `/snap/jenkins` and run:

```bash
java -jar jenkins.war --httpPort=<port_number>
```
