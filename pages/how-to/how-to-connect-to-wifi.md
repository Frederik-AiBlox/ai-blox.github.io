---
layout: default
title: How to connect to WiFi
parent: How to
nav_order: 4
has_children: false
has_toc: false
---

# How to connect your Blox to a Wifi network

This page descirbes how to configure and connect to a WiFi network

### Check the WiFi 

Lookup the WiFi interface name

```bash
$ nmcli d
```
As the WiFi is not yet connected to any network, the output shows a disconnected state

```bash
DEVICE   TYPE      STATE         CONNECTION
eth0     ethernet  connected     Wired connection 1
docker0  bridge    connected     docker0
 wlan0    wifi      disconnected  -- 
```

### Check for available WiFi Networks

```bash
$ nmcli d wifi list
```
The output will be a list of available networks. An check if the desired network is listed in the output.

```bash
IN-USE  SSID                    MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        Some Public Wi-Fi   Infra  13    130 Mbit/s  100     ▂▄▆█  WPA2 802.1X
        A-Home-4E18         Infra  104   540 Mbit/s  100     ▂▄▆█  WPA2
        Another-Home-4E19   Infra  13    130 Mbit/s  74      ▂▄▆_  WPA2
```
To exit this you can a few times the `enter` key or by `ctrl` + `c` command

### Connect to the Wifi Network

Now a connection to the WiFi Network can be established. The `SSID` will come out of the output of the `nmcli d wifi list` and you will need to provide the network password. 

In the command below, replace 
- `your_wifi_network_SSID` with the SSID of the preferred network
- `your_wifi_password` with the your password

```bash
$ sudo nmcli d wifi connect your_wifi_network_SSID password your_wifi_password
```

The output will indicate that a connection to the Wifi network is established. 

Additionally, the status can be checked, by the `nmcli d` command, used in the first step

```bash
$ nmcli d
```

The output shows the connected state of the WiFi along with the SSID of the network

```bash
DEVICE   TYPE      STATE        CONNECTION
eth0     ethernet  connected    Wired connection 1
wlan0    wifi      connected    A-Home-4E18 1
docker0  bridge    connected    docker0
```