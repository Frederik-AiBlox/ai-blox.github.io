---
layout: default
title: 6-Channel MIPI interface
parent: Interface Modules
nav_order: 2
---

# 6-Channel MIPI interface

The 6-Channel MIPI interface module allows you to connect up to 6 MIPI cameras.

---

## Description

The MXxxx allows you to connect up to 6 MIPI cameras to the MODULE-X device. 
The maximum number of cameras depends on the Jetson Module. 
For the Jetson Nano, you can only connect up to 3 cameras. 
For the Jetson TX2 NX and the Jetson Xavier NX, you can connect up to 6 cameras.

The module has also a debug interface which makes the module ideal as a development module for your application. 
The debug interface consist out of an USB connection to flash the module and a serial port which allows you to monitor the boot terminal output.
To flash the module, you need to press the recovery button while turning the power on. 
The recovery button is also available on the module.

## Block diagram

<p align="center">
<img src="/assets/images/pages/interface-modules/6-channel-mipi/BlockDiagram.svg" width="300">
</p>

The above diagram shows the block diagram of the interface module. At the top, we have 3 connectors:
* Power connector for powering the MODULE-X device
* Serial connector for connecting the boot terminal 
* USB connector for flashing the MODULE-X device

There is an button on the module, which allows you to place the MODULE-X in recovery mode.
When the device is in recovery mode, you can flash the Jetson module through the USB.

There are in total 6 FPC connectors for connecting the cameras. 
Those connectors are compatible with the Raspberry Pi camera connector. 
Each camera has it's own 2-lane MIPI channel. 


## Connections

### Raspberry Pi camera connector 

The connector type used on the module is the [1-1734248-5](https://www.te.com/usa-en/product-1-1734248-5.html?te_campaign=oct_glo_manufacturer&elqCampaignId=26136&te_bu=Cor&te_type=other) connector from TE Connectivity.

| Pin# | Pin Name  | Description               |
|:-----|:----------|:--------------------------|
| 1    | GND       | Ground                    |
| 2    | CSI_D0_N  | MIPI Data Lane 0 Negative |
| 3    | CSI_D0_P  | MIPI Data Lane 0 Positive |
| 4    | GND       | Ground                    |
| 5    | CSI_D1_N  | MIPI Data Lane 1 Negative |
| 6    | CSI_D1_P  | MIPI Data Lane 1 Positive |
| 7    | GND       | Ground                    |
| 8    | CSI_CLK_N | MIPI Clock Lane Negative  |
| 9    | CSI_CLK_P | MIPI Clock Lane Positive  |
| 10   | GND       | Ground                    |
| 11   | CAM_PWDN  | CAM Power Down            |
| 12   | CAM_MCLK  | CAM Master CLock          |
| 13   | GND       | I2C SCL                   |
| 14   | GND       | I2C SDA                   |
| 15   | GND       | 3.3V Power                |

### Debug interface

The debug interface is compatible with the [TTL-232R-3V3](https://ftdichip.com/products/ttl-232r-3v3/) cable from FTDI-chip.
Pin 1 is the black cable on the connector.

| Pin# | Pin Name  | Description               |
|:-----|:----------|:--------------------------|
| 1    | GND       | Ground (Black)            |
| 2    | NC        | Not Connected             |
| 3    | NC        | Not Connected             |
| 4    | TXD       | Transmit (3V3)            |
| 5    | RXD       | Receive (3V3)             |
| 6    | NC        | Not Connected             |