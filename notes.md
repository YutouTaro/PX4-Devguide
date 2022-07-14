This work is based on the official website of PX4 Development Guide (v1.11.0), available at [Introduction · PX4 Developer Guide](https://dev.px4.io/v1.11_noredirect/en/)

* # Versions of softwares/packages
  
  * QGroundControl <u>V4.1.7</u>
  
  * 

* # Getting Started

# Initial Setup

## Basic Equipment

* Taranis Plus remote control 
  
  * X9D Plus

* A development computer

* also used as the ground control station device

# Toolchain Installation

> **Ubuntu**
> 
> For other OS, please refer to [Toolchain Installation #Development Environment](https://dev.px4.io/v1.11_noredirect/en/setup/dev_env.html#development-environment)

## Gazebo, JMAVSim and NuttX (Pixhawk) Targets

Install the toolchain

```bash
# Download PX4 Source Code
git clone https://github.com/PX4/Firmware.git --recursive

# Run the ubuntu.sh with no arguments to install
cd Firmware
bash ./Tools/setup/ubuntu.sh
```

verify the the **NuttX** installation by confirming the gcc version

`arm-none-eabi-gcc --version`

> ```
> arm-none-eabi-gcc (GNU Tools for Arm Embedded Processors 7-2017-q4-major) 7.2.1 20170904 (release) [ARM/embedded-7-branch revision 255204]
>  Copyright (C) 2017 Free Software Foundation, Inc.
>  This is free software; see the source for copying conditions.  There is NO
>  warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
> ```

## Visual Studio

Visual Studio is recommended in the official document

1. Download VSCode for your OS

2. add PX4 source code to VSCode
   
   (<u>top menu</u>) `File`>`Open Folder`
   
   select `Firmware` directory

3. Install extensions
   
   * When opening folder for the first time, a prompt on the bottom right will recommend you the extensions
   
   * Or, it can be found by clicking the `Extensions` icon on the <u>left side</u>, and keying in `@recommended` in the search bar. Click the "download from cloud" icon under the search bar to install. 
   
   * 
