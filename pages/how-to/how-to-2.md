---
layout: default
title: How to start with a BLOX
parent: How to
nav_order: 3
has_children: true
has_toc: false
---

# How-to find start with a BLOX

This page describe how you can start with a BLOX

---

# Introduction

We get quite often the question how to start with a BLOX.

In this how-to, we will give a guideline for your first steps exploring the BLOX platform.

## Prerequisites
* Any BLOX with a gigabit ethernet communication module

# Step by step guide

## Step 1: finding the IP-address

When the BLOX is shipped, it needs to have an DHCP server for getting a dynamic IP address.
Therefore the BLOX needs to be connect to a DHCP server through the gigabit ethernet communication module?

> In case you have a BLOX with an IB-03xx (4-Channel 100Mb Ethernet interface module), don't use one of the 4 ethernet ports on this module to connect the router.
> Those ports aren't configured to receive a dynamic IP address.

## Step 2: make a ssh connection

You can make an ssh connection with the BLOX with the command below.
The standard user name is: ai-blox and password: ai-blox.

````shell
$ ssh ai-blox@xxx.xxx.xxx.xxx
````
where xxx.xxx.xxx.xxx is the IP-address found in step-1.

## Step 4: make a VNC connection

To connect through VNC with the BLOX, you need to have a VNC client installed on your computer.
The standard login credentials are the same as for ssh. (user: ai-blox, password: ai-blox)