---
layout: default
title: Kernel
parent: MODULE-X
nav_order: 3
---

# Kernel

AI-BLOX has done some modification on the kernel and device tree to support the MODULE-X device, the interface and comm modules.
This chapter describes how you can rebuild the kernel by yourself.

## Obtaining the AI-BLOX Kernel Sources and build it

### Prerequisites

* Have a Ubuntu system with version Ubuntu 18.04.06 LTS

* You have too install Git. Install Git with the following command:
  
      $ sudo apt install git-core

* You have too install the utilities required by the kernel build process:

      $ sudo apt install build-essential bc

* You have too install the Jetson Linux Toolchain:

      $ mkdir $HOME/l4t-gcc
      $ cd $HOME/l4t-gcc
      $ wget http://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/aarch64-linux-gnu/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz
      $ tar xf gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz
      $ rm gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz

### To sync the kernel sources

* Clone the l4t repository:

      $ git clone https://github.com/ai-blox/l4t.git

* Get the kernel source by running the `source_sync.sh` script:

      $ cd l4t 
      $ ./source_sync.sh -t modx-l4t-r32.4.3

### To build the AI-BLOX Kernel

1. Set the shell variable with the command:

       $ TEGRA_KERNEL_OUT=<outdir>

2. Export following environment variables for cross-compiling:

       $ export CROSS_COMPILE=$HOME/l4t-gcc/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu/bin/aarch64-linux-gnu-
       $ export LOCALVERSION=-tegra

3. Execute following commands to create the `.config` file:

        $ cd <source_dir>/l4t/sources/kernel/kernel-4.9
        $ mkdir -p $TEGRA_KERNEL_OUT
        $ make ARCH=arm64 O=$TEGRA_KERNEL_OUT tegra_defconfig

   Where ``<source_dir>`` is the directory where you cloned the ai-blox/l4t repository. 

4. Execute the following commands to build the kernel including DTBs and modules:

        $ make ARCH=arm64 O=$TEGRA_KERNEL_OUT -j<n>

    Where ``<n>`` indicates the number of parallel processes to be used. A typical value is the number of CPUs in your system.