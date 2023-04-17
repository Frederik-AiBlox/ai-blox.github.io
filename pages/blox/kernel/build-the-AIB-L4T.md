---
layout: default
title: Build the AIB-L4T
parent: Kernel
grand_parent: BLOX
has_children: false
nav_order: 1
---


# Build the AIB-L4T

We have created a fork of the original NVIDIA L4T repo to build our own kernel + device tree. 

This page will tell how to build the repo.

## Clone aib-l4t repo

```bash
$ git clone git@github.com:ai-blox/aib-l4t.git
$ cd aib-l4t
$ git submodule init
$ git submodule update
```

## Checkout right version

You can find the different version in the [README.md](http://README.md) file:

```bash
$ git submodule foreach 'git checkout aib-l4t-r32.7.1'
```

## Build the kernel

```bash
$ cd kernel/kernel-4.9
$ export TEGRA_KERNEL_OUT=~/nvidia/ai-blox_sdk/aib-l4t-r32.7.1
$ mkdir -p $TEGRA_KERNEL_OUT
$ make ARCH=arm64 O=$TEGRA_KERNEL_OUT tegra_defconfig

# add the EDT FocalTech FT5x06 I2C Touchscreen support driver through menuconfg
# TOUCHSCREEN_EDT_FT5X06
$ make ARCH=arm64 O=$TEGRA_KERNEL_OUT menuconfig

# build everything
$ make ARCH=arm64 O=$TEGRA_KERNEL_OUT -j6
```

## Install the kernel + device trees

```bash
$ export TEGRA_SDK_PATH=~/nvidia/nvidia_sdk/JetPack_4.6.1_Linux_JETSON_XAVIER_NX_TARGETS/Linux_for_Tegra
$ export TEGRA_SDK_KERNEL_PATH=$TEGRA_SDK_PATH/kernel
$ export TEGRA_SDK_ROOTFS_PATH=$TEGRA_SDK_PATH/rootfs
 
$ cp $TEGRA_KERNEL_OUT/arch/arm64/boot/Image $TEGRA_SDK_KERNEL_PATH
$ sudo cp $TEGRA_KERNEL_OUT/arch/arm64/boot/dts/tegra194-p3668-all-mx1030-2.dtb $TEGRA_SDK_ROOTFS_PATH/boot
$ sudo make ARCH=arm64 O=$TEGRA_KERNEL_OUT INSTALL_MOD_PATH=$TEGRA_SDK_ROOTFS_PATH modules_install
```

<!-- # Toolchain

Switch between JetPack 4.x toolchain and JetPack 5.x:

```bash
# JetPack 4.x
$ export CROSS_COMPILE=~/l4t-gcc/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu/bin/aarch64a-linux-gnu-

# JetPack 5.x
$ export CROSS_COMPILE=~
``` -->