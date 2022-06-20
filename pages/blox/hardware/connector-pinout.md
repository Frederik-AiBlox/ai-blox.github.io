---
layout: default
title: Connector pinout
parent: Hardware
grand_parent: BLOX
nav_order: 2
has_toc: false
---

# Connector pinout

The MODULE-X device has 3 extension connectors. 2 for the interface slot and one for the communication slot.

![](/assets/images/pages/module-x/ConnectorPinout.svg)

## Interface connector A

| Jetson    || Interface Connector B                     |||| Jetson           ||
| Name       | Pin# | Name       | Pin#       || Name       | Pin# | Name       |
|:----------:|:----:|:----------:|:----:|:----:|:----------:|:----:|:----------:|
|            |      | GND        | 1    | 2    | GND        |      |            |
| SPI0_MOSI  | 89   | SPI0_MOSI  | 3    | 4    | SPI1_MOSI  | 104  | SPI1_MOSI  |
| SPI0_SCK   | 91   | SPI0_SCK   | 5    | 6    | SPI1_SCK   | 106  | SPI1_SCK   |
| SPI0_MISO  | 93   | SPI0_MISO  | 7    | 8    | SPI1_MISO  | 108  | SPI1_MISO  |
| SPI0_CS0   | 95   | SPI0_CS0   | 9    | 10   | SPI1_CS0   | 110  | SPI1_CS0   |
| SPIO_CS1   | 97   | SPIO_CS1   | 11   | 12   | SPI1_CS1   | 112  | SPI1_CS1   |
|            |      | GND        | 13   | 14   | GND        |      |            |
| USBSS_RX_N | 161  | USBSS_RX_N | 15   | 16   | USBSS_TX_N | 166  | USBSS_TX_N |
| USBSS_RX_P | 162  | USBSS_RX_P | 17   | 18   | USBSS_TX_P | 168  | USBSS_TX_P |
|            |      | GND        | 19   | 20   | GND        |      |            |
| USB2_D_N   | 121  | USB2_D_N   | 21   | 22   | USB13_D_N  | Internal USB Hub ||
| USB2_D_P   | 123  | USB2_D_P   | 23   | 24   | USB13_D_P  | Internal USB Hub ||
|            |      | GND        | 25   | 26   | GND        |      |            |
| CAN_RX     | 143  | CAN_RX     | 27   | 28   | I2C0_SCL   | 185  | I2C0_SCL   |
| CAN_TX     | 145  | CAN_TX     | 29   | 30   | I2C0_SDA   | 187  | I2C0_SDA   |
|            |      | GND        | 31   | 32   | GND        |      |            |
|            |      | GND        | 33   | 34   | I2C1_SCL   | 189  | I2C1_SCL   |
|            |      | GND        | 35   | 36   | I2C1_SDA   | 191  | I2C1_SDA   |
|            |      | GND        | 37   | 38   | GND        |      |            |
| I2S0_DOUT  | 193  | I2S0_DOUT  | 39   | 40   | I2S1_DOUT  | 220  | I2S1_DOUT  |
| I2S0_DIN   | 195  | I2S0_DIN   | 41   | 41   | I2S1_DIN   | 222  | I2S1_DIN   |
| I2S0_FS    | 197  | I2S0_FS    | 43   | 44   | I2S1_FS    | 224  | I2S1_FS    |
| I2S0_SCLK  | 199  | I2S0_SCLK  | 45   | 46   | I2S1_SCLK  | 226  | I2S1_SCLK  |
|            |      | GND        | 47   | 48   | GND        |      |            |
| GPIO01     | 118  | GPIO01     | 49   | 50   | GPIO07     | 206  | GPIO07     |
| GPIO02     | 124  | GPIO02     | 51   | 52   | GPIO08     | 208  | GPIO08     |
| GPIO03     | 126  | GPIO03     | 53   | 54   | GPIO09     | 211  | GPIO09     |
| GPIO04     | 127  | GPIO04     | 55   | 56   | GPIO10     | 212  | GPIO10     |
| GPIO05     | 128  | GPIO05     | 57   | 58   | GPIO11     | 216  | GPIO11     |
| GPIO06     | 130  | GPIO06     | 59   | 60   | GPIO12     | 218  | GPIO12     |
|            |      | GND        | 61   | 62   | GND        |      |            |
|            |      | GND        | 63   | 64   | GND        |      |            |
| UART2_RXD  | 238  | UART2_RXD  | 65   | 66   | USB0_D_N   | 109  | USB0_D_N   |
| UART2_TXD  | 236  | UART2_TXD  | 67   | 68   | USB0_D_P   | 111  | USB0_D_P   |
|            |      | GND        | 69   | 70   | GND        |      |            |
| GPIO00     | 87   | GPIO00     | 71   | 72   | FORCE_REC  | 214  | FORCE_REC  |
|            |      | VIN        | 73   | 74   | VIN        |      |            |
|            |      | VIN        | 75   | 76   | VIN        |      |            |
|            |      | VIN        | 77   | 78   | VIN        |      |            |
|            |      | SHIELD     | 79   | 80   | SHIELD     |      |            |

## Interface connector B

| Jetson    || Interface Connector A                     |||| Jetson           ||
| Name       | Pin# | Name       | Pin#       || Name       | Pin# | Name       |
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

## Comm connector A

| Jetson      || Comm Connector 1                              |||| Jetson             ||
| Name         | Pin# | Name         | Pin#       || Name         | Pin# | Name         |
|:------------:|:----:|:------------:|:----:|:----:|:------------:|:----:|:------------:|
|              |      | GND          | 1    | 2    | GND          |      |              |
| GBE_MDI1_P   | 192  | GBE_MDI1_P   | 3    | 4    | GBE_MDI2_P   | 198  | GBE_MDI4_P   |
| GBE_MDI1_N   | 190  | GBE_MDI1_N   | 5    | 6    | GBE_MDI2_N   | 196  | GBE_MDI4_N   |
|              |      | GND          | 7    | 8    | GND          |      |              |
| GBE_MDI0_P   | 186  | GBE_MDI0_P   | 9    | 10   | GBE_MDI3_P   | 204  | GBE_MDI3_P   |
| GBE_MDI0_N   | 184  | GBE_MDI0_N   | 11   | 12   | GBE_MDI3_N   | 202  | GBE_MDI3_N   |
|              |      | GND          | 13   | 14   | GND          |      |              |
| GBE_LED_LINK | 188  | GBE_LED_LINK | 15   | 16   | GBE_LED_ACT  | 194  | GBE_LED_ACT  |
|              |      | GND          | 17   | 18   | GND          |      |              |
| PCIE0_TX3_P  | 156  | PCIE0_TX3_P  | 19   | 20   | PCIE0_RX3_P  | 157  | PCIE0_RX3_P  |
| PCIE0_TX3_N  | 154  | PCIE0_TX3_N  | 21   | 22   | PCIE0_RX3_N  | 155  | PCIE0_RX3_N  |
|              |      | GND          | 23   | 24   | GND          |      |              |
| PCIE0_TX2_P  | 150  | PCIE0_TX2_P  | 25   | 26   | PCIE0_RX2_P  | 151  | PCIE0_RX2_P  |
| PCIE0_TX2_N  | 148  | PCIE0_TX2_N  | 27   | 28   | PCIE0_RX2_N  | 149  | PCIE0_RX2_N  |
|              |      | GND          | 29   | 30   | GND          |      |              |
|  PCIE0_TX1_P | 142  | PCIE0_TX1_P  | 31   | 32   | PCIE0_RX1_P  | 139  | PCIE0_RX1_P  |
|  PCIE0_TX1_N | 140  | PCIE0_TX1_N  | 33   | 34   | PCIE0_RX1_N  | 137  | PCIE0_RX1_N  |
|              |      | GND          | 35   | 36   | GND          |      |              |
| PCIE0_TX0_P  | 136  | PCIE0_TX0_P  | 37   | 38   | PCIE0_RX0_P  | 133  | PCIE0_RX0_P  |
| PCIE0_TX0_N  | 134  | PCIE0_TX0_N  | 39   | 40   | PCIE0_RX0_N  | 131  | PCIE0_RX0_N  |
|              |      | GND          | 41   | 41   | GND          |      |              |
| PCIE0_CLK_P  | 162  | PCIE0_CLK_P  | 43   | 44   | USB12_D_P    | Internal USB Hub   ||
| PCIE0_CLK_N  | 160  | PCIE0_CLK_N  | 45   | 46   | USB12_D_N    | Internal USB Hub   ||
|              |      | GND          | 47   | 48   | GND          |      |              |
| PCIE0_WAKE   | 179  | PCIE0_WAKE   | 49   | 50   | UART1_CTS    | 209  | UART1_CTS    |
| PCIE0_RST    | 181  | PCIE0_RST    | 51   | 52   | UART1_RTS    | 207  | UART1_RTS    |
| PCIE0_CLKREQ | 180  | PCIE0_CLKREQ | 53   | 54   | UART1_RXD    | 205  | UART1_RXD    |
|              |      | NC           | 55   | 56   | UART1_TXD    | 203  | UART1_TXD    |
|              |      | NC           | 57   | 58   | GND          |      |              |
|              |      | NC           | 59   | 60   | I2C_SDA      | 234  | I2C_SDA      |
|              |      | NC           | 61   | 62   | I2C_SCL      | 232  | I2C_SCL      |
|              |      | GND          | 63   | 64   | GND          |      |              | 
|              |      | GND          | 65   | 66   | GND          |      |              |
|              |      | VDD_5V       | 67   | 68   | VDD_5V       |      |              |
|              |      | VDD_5V       | 69   | 70   | VDD_5V       |      |              |
|              |      | GND          | 71   | 72   | GND          |      |              |
|              |      | GND          | 73   | 74   | GND          |      |              |
|              |      | VDD_3V3      | 75   | 76   | VDD_3V3      |      |              |
|              |      | VDD_3V3      | 77   | 78   | VDD_3V3      |      |              |
|              |      | NC           | 79   | 80   | NC           |      |              |
