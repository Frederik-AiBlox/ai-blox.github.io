---
layout: default
title: Connector pinout
parent: MODULE-X
nav_order: 2
---

# Connector pinout

The MODULE-X device has 3 extension connectors. 2 for the interface slot and one for the communication slot.

![](/assets/images/pages/module-x/ConnectorPinout.svg)

## Interface connector A

<style>
    th, td { min-width: auto; }
</style>

| Jetson    || Interface Connector A                     |||| Jetson           ||
| Name       | Pin# | Name       | Pin# | Pin# | Name       | Pin# | Name       |
|:----------:|:----:|:----------:|:----:|:----:|:----------:|:----:|:----------:|
|            |      | GND        | 1    | 2    | GND        |      |            |
| CSI0_CLK_N | 10   | CSI0_CLK_N | 3    | 4    | CSI2_CLK_N | 28   | CSI2_CLK_N |
| CSI0_CLK_P | 12   | CSI0_CLK_P | 5    | 6    | CSI2_CLK_P | 30   | CSI2_CLK_P |
|            |      | GND        | 7    | 8    | GND        |      |            |
| CSI0_D0_N  | 4    | CSI0_D0_N  | 9    | 10   | CSI2_D0_N  | 22   | CSI2_D0_N  |
| CSI0_D0_P  | 6    | CSI0_D0_P  | 11   | 12   | CSI2_D0_P  | 24   | CSI2_D0_P  |
|            |      | GND        | 13   | 14   | GND        |      |            |
| CSI0_D1_N  | 16   | CSI0_D1_N  | 15   | 16   | CSI2_D1_N  | 34   | CSI2_D1_N  |
| CSI0_D1_P  | 18   | CSI0_D1_P  | 17   | 18   | CSI2_D1_P  | 36   | CSI2_D1_P  |
|            |      | GND        | 19   | 20   | GND        |      |            |
| CSI1_CLK_N | 9    | CSI1_CLK_N | 21   | 22   | CSI3_CLK_N | 27   | CSI3_CLK_N |
| CSI1_CLK_P | 11   | CSI1_CLK_P | 23   | 24   | CSI3_CLK_P | 29   | CSI3_CLK_P |
|            |      | GND        | 25   | 26   | GND        |      |            |
| CSI1_D0_N  | 3    | CSI1_D0_N  | 27   | 28   | CSI3_D0_N  | 21   | CSI3_D0_N  |
| CSI1_D0_P  | 5    | CSI1_D0_P  | 29   | 30   | CSI3_D0_P  | 23   | CSI3_D0_P  |
|            |      | GND        | 31   | 32   | GND        |      |            |
| CSI1_D1_N  | 15   | CSI1_D1_N  | 33   | 34   | CSI3_D1_N  | 33   | CSI3_D1_N  |
| CSI1_D1_P  | 17   | CSI1_D1_P  | 35   | 36   | CSI3_D1_P  | 35   | CSI3_D1_P  |
|            |      | GND        | 37   | 38   | GND        |      |            |
| CSI4_CLK_N | 52   | CSI4_CLK_N | 39   | 40   | DSI_CLK_N  | 76   | DSI_CLK_N  |
| CSI4_CLK_P | 54   | CSI4_CLK_P | 41   | 41   | DSI_CLK_P  | 78   | DSI_CLK_P  |
|            |      | GND        | 43   | 44   | GND        |      |            |
| CSI4_D0_N  | 46   | CSI4_D0_N  | 45   | 46   | DSI_D0_N   | 70   | DSI_D0_N   |
| CSI4_D0_P  | 48   | CSI4_D0_P  | 47   | 48   | DSI_D0_P   | 73   | DSI_D0_P   |
|            |      | GND        | 49   | 50   | GND        |      |            |
| CSI4_D1_N  | 58   | CSI4_D1_N  | 51   | 52   | DSI_D1_N   | 82   | DSI_D1_N   |
| CSI4_D1_P  | 60   | CSI4_D1_P  | 53   | 54   | DSI_D1_P   | 84   | DSI_D1_P   |
|            |      | GND        | 55   | 56   | GND        |      |            |
| CSI4_D2_N  | 40   | CSI4_D2_N  | 57   | 58   | CAM_I2C_SCL | 213 | CAM_I2C_SCL |
| CSI4_D2_P  | 42   | CSI4_D2_P  | 59   | 60   | CAM_I2C_SDA | 215 | CAM_I2C_SDA |
|            |      | GND        | 61   | 62   | CAM0_PWDN  | 114  | CAM0_PWDN  |
| CSI4_D3_N  | 64   | CSI4_D3_N  | 63   | 64   | CAM0_MCLK  | 116  | CAM0_MCLK  |
| CSI4_D3_P  | 66   | CSI4_D3_P  | 65   | 66   | CAM1_PWDN  | 120  | CAM1_PWDN  |
|            |      | GND        | 67   | 68   | CAM1_MCLK  | 122  | CAM1_MCLK  |
|            |      | GND        | 69   | 70   | GND        |      |            |
|            |      | VDD_3V3    | 71   | 72   | VDD_3V3    |      |            |
|            |      | VDD_3V3    | 73   | 74   | VDD_3V3    |      |            |
|            |      | GND        | 75   | 76   | GND        |      |            |
|            |      | VDD_5V     | 77   | 78   | VDD_5V     |      |            |
|            |      | VDD_5V     | 79   | 80   | VDD_5V     |      |            |

## Interface connector B

## Communication connector A
