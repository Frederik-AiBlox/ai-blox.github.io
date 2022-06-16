---
layout: default
title: Kernel Support
parent: BLOX
has_children: true
nav_order: 3
---


# Device tree

Each BLOX has it's own device tree. The table below shows the root device tree.



| Device   | Filename                               | Description                            |
|----------|----------------------------------------|----------------------------------------|
| MX1010-1 | tegra210-p3448-0002-MX1010-1-***ver***.dts | BLOX, Jetson Nano                  |
| MX1010-2 | tegra210-p3448-0002-MX1010-2-***ver***.dts | BLOX, Jetson Nano, 7" touch screen |
| MX1020-1 |  | BLOX, Jetson TX2 NX |
| MX1020-2 |  | BLOX, Jetson TXZ NX, 7" touch screen |
| MX1030-1 | tegra194-p3668-0001-MX1030-1-***ver***.dts | BLOX, Jetson Xavier NX |
| MX1030-2 | tegra194-p3668-0001-MX1030-2-***ver***.dts | BLOX, Jetson Xavier NX, 7" touch screen|


# Jetson Linux Toolchain

NVIDIA speciffies the Linaro gcc 7.3.1 2018.05 aarch toolchain.

## Downloading the Toolchain

```shell
http://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/aarch64-linux-gnu/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz
```

## Extracting the Toolchain

```shell
$ mkdir $HOME/l4t-gcc
$ cd $HOME/l4t-gcc
$ tar xf gcc-linaro-7.3.ht-install-a-sim-card-2018.05-x86_64_aarch64-linux-gnu.tar.xz
```

## Setting the CROSS_COMPILE Environment Variable

```shell
$ export CROSS_COMPILE=$HOME/l4t-gcc/gcc-linaro-7.3.ht-install-a-sim-card-2018.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-
```