---
layout: default
title: Quickstart
nav_order: 1
has_children: true
has_toc: true
---

# Quickstart

# Intro

To get up and running wiht your Ai-Blox device, we will first connect to it over ssh or a VNC client.

**What is included in the box?**
- an Ai-Blox device with pre-mounted Communication module (Green) and Interface module (Red) of your preferrence
- Blox power supply
- Ai-Blox programmer

We already have flashed the blox device and SD-card with Ubuntu version 18.04.6 LTS and JetPack 4.6.1. The SD card is already placed into its holder in the device.

**What else do you need?**
- an Ethernet cable
- a LAN network connection with DHCP
- a network connected computer with perferrable Ubuntu, Windows could do the trick too...
- a power cable

# Step 1: Connect the programmer

Before powering on the Blox, the programmer needs to be connected. The connection pads on the PCB can be found underneath the communication module.

1. Remove the red cover of the communication module

For removing the communication module cover, you need to unscrew the 2 screws as showed below with an alley key.

If there is a WiFi or LTE modem mounted, you will have to unscrew this also. 

2. Connecting the Programmer

Connect the  



# Step 1: Power on

Before powering the device, it is convenient to first connect your Ethernet cable to the GigE Ethernet of the red communication module (CB-0010, CB-0110 or CB). By default the Blox Ethernet is configured to receive a dynamic IP address from the DHCP server on your network. 


![Blox-EthernetConnected](/assets/images/pages/getting-started/Blox-Eth-Connected.png)

*If your blox device has the CB-0310 (4 PoE Ethernet) green communication module, note that these are not configured by default to receive a dynamic IP address. Do not use these ports to conenct to your network.*

Plug in the Power supply connector. The boot time of the blox is around 30s. The RJ45 status leds will indicate that there is a link (left LED) and activity (right LED).



# Step 2: Find the IP address


To be able to connect to the Blox over ssh or VNC, the IP address has be to be found. The blox will have received a dynamic IP address from the DHCP server on your network. 
There are several options to discover the IP address: network scanning with nmap and arp or using the Blox Programmer USB to Serail Port.   

## Network scanning using nmap

Nmap or network mapper is an open-source tool to scan a network. It can be used to retreive the IP addresses of devices on the network. 

In the command below, replace the x with the subnet your computer is in and make sure the Blox will recieve a IP address in that same subnet.
```bash
$ sudo nmap -sn 192.168.x.0/24
```

Nmap will output a list of IP addresses. To find your Blox device look for the `tegra-ubuntu`.

If nmap is not recognised, then you will need to install it first.
```bash 
$ sudo apt update
$ sudo apt install nmap
```

## 


### Blox programmer serial console

The Blox Programmer device contains a USB to Serial Port Bridge and can be used to connect to the serial console of the Blox platform. 

#### Ubuntu

Connect the programmer's USB cable to your computer. Connect the tag connector the Blox. 

Find the serial port on your computer
```bash
$ ls  /dev/tty*
```
The serial port will appear as ttyUSBx in the above command output. If it is the only USB to serial convertor connected to your computer it will be listed as ttyUSB0.

Start the serial connection

To use the serial connection you will use the screen command. If you are not sure if screen is installed on your computer, you can always test with following command. 
```bash
$ screen -v
```
If the output from the above command is ```Command 'screen' not found```, you will need to install screen, otherwise you can skip this step.
```bash
$ sudo apt install screen
```
Start the serial port
```
$ sudo screen /dev/ttyUSB0 115200
```
The console screen will be cleared. Now power on the Blox. 

From the moment the blox is powered, the boot log will appear in the terminal running screen. 
The boot log will stop to ask you to login.

```bash
Ubuntu 18.04.6 LTS tegra-ubuntu ttyTCU0
tegra-ubuntu login:
```
Now login with `ai-blox`
```
Password:
```
Password is `









Power on the Blox.








- programmer device => login => command  
- 
$ ifconfig | grep inet
    inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
    inet 192.168.1.53  netmask 255.255.255.0  broadcast 192.168.1.255
    inet6 fe80::7bbf:599a:3f35:6a6d  prefixlen 64  scopeid 0x20<link>
    inet6 2a02:a03f:6997:a000:1d20:bc8b:30a8:106  prefixlen 64  scopeid 0x0<global>
    inet6 2a02:a03f:6997:a000:6ea8:c046:e67a:9cf9  prefixlen 64  scopeid 0x0<global>
    inet 127.0.0.1  netmask 255.0.0.0
    inet6 ::1  prefixlen 128  scopeid 0x10<host>


Using the programmer with Windows => link to install of Windows driver












