---
layout: default
title: Stress test
parent: Hardware
grand_parent: MODULE-X
nav_order: 1
has_toc: false
---

# Stress Test
How to push the MODULE-X to the limits?

---
## Introduction

The MODULE-X is passive cooled. 
This means that the device doesn't have a fan to cool down.
The device is cooled down with natural airflow flowing over the well designed heat sink.
At least, that's the theory 😅. 
In this chapter, we will explain how you can stress the MODULE-X to the limits and verify if the module withstand the temperature specs.

## Prerequisites

* You need one of the following modules:
   * [IMX1010-1](https://www.ai-blox.com/shop/10-10-0001-mx1010-1-1), MODULE-X with Jetson Nano
   * [IMX1020-1](https://www.ai-blox.com/shop/10-20-0001-mx1020-1-20), MODULE-X with Jetson TX2 NX
   * [IMX1030-1](https://www.ai-blox.com/shop/10-30-0001-mx1030-1-22), MODULE-X with Jetson Xavier NX

## Install tools

* Install the `stress` tool for CPU stressing:
```bash
$ sudo apt-get update
$ sudo apt-get install -y stress
```

* Install CUDA necessary to stress the GPU, there are 2 options:
  * through the NVIDIA software SDK
  * through deb installation package, this procedure is showed below for JetPack 4.6

```shell
$ wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/sbsa/cuda-ubuntu1804.pin
$ sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
$ sudo apt-get update
wget https://repo.download.nvidia.com/jetson/common/pool/main/c/cuda-toolkit-10-2/cuda-toolkit-10-2_10.2.460-1_arm64.deb
sudo apt install ./cuda-toolkit-10-2_10.2.460-1_arm64.deb
```

* Build the matrixMul sample app:

```shell
$ cd /usr/local/cuda/samples/0_Simple/matrixMul
$ sudo make
```

## Run test

For getting the maximum performance out of the Jetson Modules, three things need to be done:
* Chose your power mode for the test
* Run the GPU at maximum performance
* Run the CPUs at maximum performance

It's good to have the test run for several hours on a constant room temperature. 
This allows the system to settle down at the maximum temperature.

Choosing the power mode depends of which module you are testing.
An overview of the available power modes can be found in the Power Mode section of this page.
cd

```bash
$ sudo /usr/sbin/nvpmodel -m <x>
```
Where `<x>` is the power mode. The maximum power modes are:
* Jetson Nano @10W: `nvpmodel -m 0` 
* Jetson TX2 NX @15W: `nvpmodel -m 3`
* Jetson Xavier NX @15W: `nvpmodel -m 2`
* Jetson Xavier NX @20W: `nvpmodel -m 8` only available with JetPack >=4.6

Run the GPU at max performance:
```bash
$ while :; do /usr/local/cuda/samples/0_Simple/matrixMul/matrixMul -wA=6400 -hA=640 -wB=640 - hB=6400; done
```

Run the CPUs at max performance:
```bash
$ stress -c $(nproc)
```

Monitor the results:
```bash
$ tegrastats
RAM 1802/7772MB (lfb 357x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@42.5C GPU@44.5C PMIC@100C AUX@43.5C CPU@44.5C thermal@44.25C VDD_IN 14703/14683 VDD_CPU_GPU_CV 10874/10893 VDD_SOC 1405/1405
RAM 1802/7772MB (lfb 357x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@42.5C GPU@45C PMIC@100C AUX@43C CPU@44.5C thermal@43.9C VDD_IN 14703/14690 VDD_CPU_GPU_CV 10874/10887 VDD_SOC 1405/1405
RAM 1802/7772MB (lfb 357x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@42.5C GPU@45C PMIC@100C AUX@43.5C CPU@45C thermal@44.05C VDD_IN 14664/14683 VDD_CPU_GPU_CV 10913/10893 VDD_SOC 1405/1405
RAM 1802/7772MB (lfb 356x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@42.5C GPU@44.5C PMIC@100C AUX@43.5C CPU@45C thermal@44.4C VDD_IN 14664/14679 VDD_CPU_GPU_CV 10913/10897 VDD_SOC 1405/140
```
## Results

### Jetson Nano

Jetson Nano in 10W mode, room temperature 20°C.

Results:
* Total power consumption: 17,4W
* CPU temp.: 48,0°C, max temp.: 97°C (delta: 49°)
* GPU temp.: 46,0°C, max temp.: 97°C (delta: 51°C)
* Max. heat sink temp.: 24,9°C

The max ambient temp. in this mode is: 65°C (20,0°C + 49,0° caped to 65°C)

```bash
RAM 2020/3964MB (lfb 19x4MB) SWAP 43/1982MB (cached 1MB) CPU [100%@1479,100%@1479,100%@1479,100%@1479] EMC_FREQ 0% GR3D_FREQ 99% PLL@41.5C CPU@48C PMIC@100C GPU@63C AO@54.5C thermal@48.25C POM_5V_GPU 8949/8742 POM_5V_IN 3227/3086 POM_5V_CPU 3148/3134
RAM 2020/3964MB (lfb 19x4MB) SWAP 43/1982MB (cached 1MB) CPU [100%@1479,100%@1479,100%@1479,100%@1479] EMC_FREQ 0% GR3D_FREQ 83% PLL@42C CPU@48C PMIC@100C GPU@46C AO@53.5C thermal@48C POM_5V_GPU 8791/8742 POM_5V_IN 3075/3086 POM_5V_CPU 3109/3134
RAM 2020/3964MB (lfb 19x4MB) SWAP 43/1982MB (cached 1MB) CPU [100%@1479,100%@1479,100%@1479,100%@1479] EMC_FREQ 0% GR3D_FREQ 99% PLL@42C CPU@48C PMIC@100C GPU@46C AO@54C thermal@48C POM_5V_GPU 8633/8742 POM_5V_IN 2956/3086 POM_5V_CPU 3148/3134
```
![](/assets/images/pages/module-x/hardware/stress-test/Nano10W.bmp)

### Jetson TX2 NX

T.B.D.

### Xavier NX

Jetson Xavier NX in 15W mode, room temperature 20°C.

Results:
* Total power consumption: 17,4W
* CPU temp.: 53,0°C, max temp.: 90,5°C (delta: 37,5°) 
* GPU temp.: 53,5°C, max temp.: 91,5°C (delta: 38,0°C)
* AUX temp.: 51,0°C, max temp.: 90,0°C (delta: 39,0°C)
* Max. heat sink temp.: 41,4°C

The max ambient temp. in this mode is: 57,5°C (20,0°C + 37,5°)

```bash
RAM 1748/7772MB (lfb 377x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@50.5C GPU@53C PMIC@100C AUX@51C CPU@53C thermal@52.35C VDD_IN 12221/13950 VDD_CPU_GPU_CV 8812/10241 VDD_SOC 1333/1412
RAM 1749/7772MB (lfb 377x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@51C GPU@53.5C PMIC@100C AUX@51C CPU@53C thermal@52.2C VDD_IN 14664/13950 VDD_CPU_GPU_CV 10874/10241 VDD_SOC 1442/1412
RAM 1749/7772MB (lfb 377x4MB) SWAP 0/3886MB (cached 0MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@51C GPU@53.5C PMIC@100C AUX@51C CPU@53C thermal@52.35C VDD_IN 14664/13951 VDD_CPU_GPU_CV 10874/10241 VDD_SOC 1444/1412
```

![](/assets/images/pages/module-x/hardware/stress-test/XavierNx15W.bmp)

Jetson Xavier NX in 20W mode, room temperature 20°C

Results:
* Total power consumption: 19,2W
* CPU temp.: 55,0°C, max temp.: 90,5°C (delta: 35,5°)
* GPU temp.: 56,0°C, max temp.: 91,5°C (delta: 35,5°C)
* AUX temp.: 55,0°C, max temp.: 90,0°C (delta: 40,0°C)
* Max. heat sink temp.: 43,1°C

The max ambient temp. in this mode is: 55,5°C (20,0°C + 35,5°)

```bash
RAM 6774/7773MB (lfb 159x4MB) SWAP 608/3887MB (cached 46MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@54.5C GPU@57C PMIC@50C AUX@55C CPU@56C thermal@55.75C
RAM 6774/7773MB (lfb 159x4MB) SWAP 608/3887MB (cached 46MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@54.5C GPU@56.5C PMIC@50C AUX@54.5C CPU@56C thermal@55.75C
RAM 6774/7773MB (lfb 159x4MB) SWAP 608/3887MB (cached 46MB) CPU [100%@1420,100%@1420,100%@1420,100%@1420,100%@1420,100%@1420] EMC_FREQ 0% GR3D_FREQ 99% AO@54.5C GPU@56.5C PMIC@50C AUX@55C CPU@56C thermal@55.75C
```

![](/assets/images/pages/module-x/hardware/stress-test/XavierNx20W.png)

## Power Mode overview

### Jetson Nano

![](/assets/images/pages/module-x/hardware/stress-test/Jetson%20Nano%20Power%20Modes.png)

### Jetson TX2 NX

![](/assets/images/pages/module-x/hardware/stress-test/Jetson%20TX2%20NX%20Power%20Modes.png)

### Jetson Xavier

![](/assets/images/pages/module-x/hardware/stress-test/Jetson%20Xavier%20NX%20Power%20Modes.png)