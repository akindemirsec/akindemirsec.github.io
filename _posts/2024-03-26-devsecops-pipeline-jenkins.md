---
layout: post
title: "Building a DevSecOps Pipeline with Jenkins & SonarQube"
date: 2024-03-26
categories: [devsecops, security]
tags: [jenkins, sonarqube, docker, ci-cd, devsecops]
excerpt: "Hands-on guide to integrating SonarQube into a Jenkins CI/CD pipeline for automated security testing, using the Vulnado vulnerable web application."
---

In this project we will integrate SonarQube in Jenkins and automate security testing with a CI/CD pipeline.

**Technologies:**
- Jenkins (Local installation)
- SonarQube (Dockerized)

We will use a vulnerable web application named [Vulnado](https://github.com/ScaleSec/vulnado) for testing.

## Jenkins Installation

There are different ways to install Jenkins but I chose the easiest way. You can install Jenkins with package managers like apt/snap or follow the [official installation guide](https://www.jenkins.io/doc/book/installing/linux/). Also you can run Jenkins on Docker but this is not preferred.

![Jenkins install](/assets/images/blog/Pasted%20image%2020240326153707.png)

## Docker Installation

We are installing Docker to run SonarQube on Docker:

![Docker install](/assets/images/blog/Pasted%20image%2020240326153728.png)

## Configuring Jenkins

After installation you can reach Jenkins's web interface from browser at `localhost:8080` (default):

![Jenkins web interface](/assets/images/blog/Pasted%20image%2020240326153755.png)

Getting the initial admin password:

![Jenkins password](/assets/images/blog/Pasted%20image%2020240326153811.png)

After you logged in, Jenkins asks which plugins to install. I chose suggested plugins:

![Plugin installation](/assets/images/blog/Pasted%20image%2020240326153828.png)

Create the first admin user:

![Admin user creation](/assets/images/blog/Pasted%20image%2020240326153843.png)

Configure the Jenkins URL:

![URL config](/assets/images/blog/Pasted%20image%2020240326153902.png)

And here's the Jenkins main page:

![Jenkins main page](/assets/images/blog/Pasted%20image%2020240326153914.png)

## Creating the Pipeline

Press "New Item", select Pipeline and give it a name:

![New pipeline](/assets/images/blog/Pasted%20image%2020240326153936.png)

In the opened page scroll down to the Pipeline section. This is the editor we are going to use:

![Pipeline editor](/assets/images/blog/Pasted%20image%2020240326153952.png)

Jenkins has a syntax for pipeline scripting. It's easy to understand and use.

### Stage 1: Install the Project

The first part of our pipeline - installing the project from Git:

![Install stage](/assets/images/blog/Pasted%20image%2020240326154104.png)

### Stage 2: Build the Project

Second part - building the project (before build: `sudo apt-get install maven -y`):

![Build stage](/assets/images/blog/Pasted%20image%2020240326154112.png)

After building, your pipeline should look like this:

![Pipeline after build](/assets/images/blog/Pasted%20image%2020240326154137.png)

## Setting Up SonarQube

We have installed and built the project in Jenkins. Now let's start security testing!

Pull the SonarQube image:

![Docker pull sonarqube](/assets/images/blog/Pasted%20image%2020240326154214.png)

Run SonarQube in a container:

![Docker run](/assets/images/blog/Pasted%20image%2020240326154219.png)

Check if it's working:

![Container running](/assets/images/blog/Pasted%20image%2020240326154243.png)

Access SonarQube at `localhost:9000` with default credentials `admin:admin`:

![SonarQube login](/assets/images/blog/Pasted%20image%2020240326154259.png)

Reset your password:

![Reset password](/assets/images/blog/Pasted%20image%2020240326154310.png)

## SonarQube Project Setup

Choose "Create a local project":

![Create project](/assets/images/blog/Pasted%20image%2020240326154325.png)

Fill the name and key:

![Project details](/assets/images/blog/Pasted%20image%2020240326154329.png)

Choose "Use global settings":

![Global settings](/assets/images/blog/Pasted%20image%2020240326154407.png)

Choose Jenkins as analysis method:

![Jenkins analysis](/assets/images/blog/Pasted%20image%2020240326154423.png)

Choose GitHub:

![GitHub integration](/assets/images/blog/Pasted%20image%2020240326154431.png)

Choose Maven - SonarQube gives us a Jenkinsfile but this script needs modification:

![Maven config](/assets/images/blog/Pasted%20image%2020240326154438.png)

## Integrating SonarQube with Jenkins

In SonarQube, go to My Account > Security > Generate new token (Global Analysis Token):

![Generate token](/assets/images/blog/Pasted%20image%2020240326154517.png)

In Jenkins Dashboard > Manage Jenkins:

![Manage Jenkins](/assets/images/blog/Pasted%20image%2020240326154536.png)

Install the SonarQube Scanner plugin:

![SonarQube plugin](/assets/images/blog/Pasted%20image%2020240326154551.png)

Go to Manage Jenkins > Credentials > Add credential:

![Add credential](/assets/images/blog/Pasted%20image%2020240326154604.png)

Select "Secret text" and paste the SonarQube Global Analysis Token:

![Secret text](/assets/images/blog/Pasted%20image%2020240326154634.png)

Manage Jenkins > System > SonarQube installations. Give a name, write the URL, and choose the token:

![SonarQube config](/assets/images/blog/Pasted%20image%2020240326154652.png)

## Final Pipeline

Your pipeline should look like this:

![Final pipeline](/assets/images/blog/Pasted%20image%2020240326154708.png)

And this is how stages should look:

![Pipeline stages](/assets/images/blog/Pasted%20image%2020240326154720.png)

And this is the SonarQube dashboard with results:

![SonarQube dashboard](/assets/images/blog/Pasted%20image%2020240326154733.png)
