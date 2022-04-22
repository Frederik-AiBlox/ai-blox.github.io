---
layout: default
title: Getting started
parent: BLOX
nav_order: 1
---

# Getting started

---

This chapter shows you step by step how to start your development on the BLOX platform.

## Prerequisites

* BLOX device with 6-Channel MIPI interface module and gigabit ethernet Module (Dev KIT)
* System running Ubuntu 18.04 
* USB Serial to TTL 3V3 cable: [TTL-232R-3V3](https://ftdichip.com/products/ttl-232r-3v3/)
* Ethernet cable


## Connect to the BLOX

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

## Camera Test

* Connect 1 or more IMX219 cameras to the BLOX. The table below shows which CAM ports are available. This depends of the Jetson Module:

| Ports      | Jetson Nano   | Jetson TX2 NX | Jetson Xavier |
|^^          |^^ MX1010-x    |^^ MX1020-x    |^^ MX1030-x    |
|:-----------|:-------------:|:-------------:|:-------------:|
| CAM0 Port  | /dev/video0   | /dev/video0   | /dev/video0   |
| CAM1 Port  |               | /dev/video1   | /dev/video1   |
| CAM2 Port  | /dev/video1   | /dev/video2   | /dev/video2   |
| CAM3 Port  |               | /dev/video3   | /dev/video3   |
| CAM4 Port  | /dev/video2   | /dev/video4   | /dev/video4   |
| CAM5 Port  |               | /dev/video5   | /dev/video5   |

* Boot the module and verify if the cameras are found:

      ai-blox@mx1010-1:~$ ls /dev/video* -all
      crw-rw----+ 1 root video 81, 0 Nov 10 09:18 /dev/video0
      crw-rw----+ 1 root video 81, 3 Nov 10 09:18 /dev/video1
      crw-rw----+ 1 root video 81, 6 Nov 10 09:18 /dev/video2

* If not all cameras are founded, you can do an extra check with following command:

      ai-blox@mx1010-1:~$ dmesg | grep imx
      [    1.715280] imx219 30-0010: tegracam sensor driver:imx219_v2.0.6
      [    1.741765] imx219 32-0010: tegracam sensor driver:imx219_v2.0.6
      [    1.768122] imx219 34-0010: tegracam sensor driver:imx219_v2.0.6
      [    1.948532] vi 54080000.vi: subdev imx219 30-0010 bound
      [    1.949398] vi 54080000.vi: subdev imx219 32-0010 bound
      [    1.950247] vi 54080000.vi: subdev imx219 34-0010 bound

* To stream a camera to your host computer, you can use following command:

      ai-blox@mx1010-1:~$ gst-launch-1.0 -e nvarguscamerasrc sensor_id=<id> ! 'video/x-raw(memory:NVMM), width=1920, height=1080, framerate=30/1' ! nvv4l2h264enc bitrate=8000000 insert-sps-pps=true ! rtph264pay mtu=1400 ! udpsink host=<host-ip> port=5000 
   
  where `<id>` is the camera which you want to stream: 0, 1, 2, 3, 4 or 5 and `<host-ip>` is your host ip-address.

* To capture the camera stream on your host computer, you can use following command:

      ai-blox@mx1010-1:~$ gst-launch-1.0 udpsrc port=5000 ! application/x-rtp,payload=96 ! rtph264depay ! avdec_h264 ! autovideosink