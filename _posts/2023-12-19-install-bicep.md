---
title: Install Azure Bicep
date: 2023-12-15 12:01:00 -500
categories: [Azure, Bicep, Tech]
tags: [azure,bicep,how to,cli,cloud]     #TAG names should always be lowercase
---

<br>

>“Everything is going to be connected to cloud and data... all of this will be mediated by software."<br>- Satya Nadella, Microsoft CEO

<br>

In this post we will setup a Bicep developer environment.

Azure Bicep was announced at Ignite 2020. Bicep is Microsoft's (DSL) Domain-Specific Language that maps 1-to-1 with (ARM) Azure Resource Manager templates. Over the years, ARM templates have become increasingly complex and burdensome. Bicep is Microsoft's answer to this problem. 

[Link](https://github.com/debauchee/barrier)

## Tasks

- [ ] Install Bicep extension for Visual Studio Code
- [ ] Install Azure CLI

1. Install Barrier from CLI

`sudo apt install barrier`

<img src="https://imgur.com/jsryfmL" alt="Install Barrier from CLI" width="100%" />

<img src="https://imgur.com/qsL6BCr" alt="Install Barrier from CLI" width="100%" />

2. Open Barrier

<img src="https://imgur.com/0t2b6bX" alt="Open Barrier" width="100%" />

3. Next on Welcome screen

<img src="https://imgur.com/Dn4phrX" alt="Next on Welcome" width="100%" />

4. Choose Server or Client

In this instance I chose Client, the other machine is acting as the Barrier Server.

<img src="https://imgur.com/PeqLJV1" alt="Choose Server or Client" width="100%" />

5. Client Settings

By default, *Auto config* will be checked. I've found that the *Auto Config* option has been hit or miss. So, I uncheck this. I have never used SSL with Barrier, seems overkill for my needs. I think it's good practice to operate software with minimal "bells and whistles," if you can get away with it. Extra features are also additional points of failure.

After unchecking *Auto config* I entered the IP address of the machine designated as the Barrier server.

Click __Start__

<img src="https://imgur.com/JRcvbbO" alt="Choose Server or Client" width="100%" />

## SSL Error

The Barrier client (Linux) did not connect to the Barrier server (Windows). The logs show some static around an ssl certificate. The Barrier Server (Windows) does not require an SSL certificate from clients, it never has. The error is originating from the client (Linux).

Checking the settings of the client (Linux), we can see *Enable SSL* is checked. I forgot this is checked by default. Whoops.

<img src="https://imgur.com/3kGjbrh" alt="Choose Server or Client" width="100%" />

*Enable SSL* turned off

<img src="https://imgur.com/ppJYQWD" alt="Choose Server or Client" width="100%" />

The log is still throwing up errors. The solution is covered in the next post.

(to be cont.)