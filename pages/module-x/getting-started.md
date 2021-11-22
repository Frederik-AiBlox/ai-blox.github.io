---
layout: default
title: Getting started
parent: MODULE-X
nav_order: 1
---

# Getting started

---

This chapter shows you step by step how to start your development on the MODULE-X platform.

## Prerequisites

* MODULE-X device with 6-Channel MIPI interface module and gigabit ethernet Module (Dev KIT)
* System running Ubuntu 18.04 
* USB Serial to TTL 3V3 cable: [TTL-232R-3V3](https://ftdichip.com/products/ttl-232r-3v3/)
* Ethernet cable


## Step by Step guide 

![](/assets/images/pages/module-x/getting-started/DevKitLayout.svg)

* Plug an ethernet cable in the ethernet port of the module. Make sure your network supports DHCP.

* Plug the [TTL-232R-3V3](https://ftdichip.com/products/ttl-232r-3v3/) to the debug port of the module. The black cable need to be at the BLK label. 

* Find the serial port on your computer:
   
      $ ls /dev/tty*
      /dev/ttyUSB0

* Open a console with the command

      $ sudo screen /dev/ttyUSB0 115200

* Power the module by plug the power jack into DC Power connector

* When the module is booted, you can login with user: `ai-blox` and password `ai-blox`:
 
      Ubuntu 18.04.5 LTS mx1020-1 ttyTCU0

      mx1020-1 login: ai-blox
      Password:
      Last login: Mon Nov 22 08:40:23 EST 2021 from 172.16.1.119 on pts/0
      Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.9.140-tegra aarch64)

      * Documentation:  https://help.ubuntu.com
      * Management:     https://landscape.canonical.com
      * Support:        https://ubuntu.com/advantage
      This system has been minimized by removing packages and content that are
      not required on a system that users do not log into.

      To restore this content, you can run the 'unminimize' command.

      319 packages can be updated.
      229 updates are security updates.

      ai-blox@mx1020-1:~$ 

* To find out the IP address of the module, you can use following command:

      ai-blox@mx1020-1:~$ ifconfig | grep inet
      inet 172.16.1.127  netmask 255.255.255.0  broadcast 172.16.1.255

* Now you can connect through ssh from your host computer, password is `ai-blox`:

       $ ssh ai-blox@172.16.1.127
       Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.9.140-tegra aarch64)

       * Documentation:  https://help.ubuntu.com
       * Management:     https://landscape.canonical.com
       * Support:        https://ubuntu.com/advantage
       This system has been minimized by removing packages and content that are
       not required on a system that users do not log into.

       To restore this content, you can run the 'unminimize' command.

       319 packages can be updated.
       229 updates are security updates.

       Last login: Mon Nov 22 08:46:32 2021 from 172.16.1.104
       ai-blox@mx1020-1:~$ 