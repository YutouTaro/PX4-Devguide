# Getting Started

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
     
     ![Install extensions](./assets/toolchain/vscode/prompt_install_extensions.jpg)
   
   * Or, it can be found by clicking the `Extensions` icon on the <u>left side</u>, and keying in `@recommended` in the search bar. Click the "download from cloud" icon under the search bar to install. 

## Fast RTPS

### Prerequirement

*     Java<a name=javasdk></a>
  
        [Java JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) is recommended, download the `rpm` file to install.
  
        [Overview of JDK Installation](https://docs.oracle.com/en/java/javase/18/install/overview-jdk-installation.html#GUID-8677A77F-231A-40F7-98B9-1FD0B48C346A)

### Install from Source

```bash
git clone --recursive https://github.com/eProsima/Fast-RTPS.git -b 1.8.x
cd FastRTPS-1.8.2
mkdir build && cd build
cmake -DTHIRDPARTY=ON -DSECURITY=ON ..
make
sudo make install # password required
```

## ~~Fast-RTPS-Gen~~

### ~~Prerequirement~~

* ~~Java SDK~~

    ~~Installed [above](#javasdk)~~

* ~~[SDKMAN!](http://sdkman.io/)~~
  
  ~~a tool for managing parallel versions of multiple Software Development Kits on most Unix-based systems~~

```bash
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

~~Check the version by~~ 

~~`sdk version`~~

~~something like this will appear~~

> ~~sdkman 5.15.0~~

* ~~Garadle~~
  
  ~~Manually install~~
  
  1. ~~[Download](https://gradle.org/releases) Gradle V4.10~~
     
     ~~Use version of 4.10 instead, as V7.5 would have the following error.~~ 
     
     > ~~Could not find method compile() for arguments [file collection] on object of type org.gradle.api.internal.artifacts.dsl.dependencies.DefaultDependencyHandler.~~ 
     
     ~~Some functions used in the code have been deprecated since Gradle 4.10.~~
  
  2. ~~Unpack the distribution~~
     
     ```bash
     sudo mkdir /opt/gradle
     sudo unzip -d /opt/gradle gradle-7.5-bin.zip
     ```
  
  3. ~~Configure system environment~~
     
     ```bash
     export PATH=$PATH:/opt/gradle/gradle-4.10/bin
     ```
  
  4. ~~Verify installation~~
     
     ~~`grade -v`~~
     
     > ~~#something~~
     > 
     > ~~\------------------------------------------------------------~~
     > 
     > ~~Gradle 4.10~~
     > 
     > ~~\------------------------------------------------------------~~
     > 
     > ~~#something~~

### ~~Install Fast-RTPS-Gen~~

```bash
git clone --recursive https://github.com/eProsima/Fast-RTPS-Gen.git -b v1.0.4
cd ~/Fast-RTPS-Gen
gradle assemble
gradle install
```

~~Failed on `gradle install`,  no permission on copying file to /usr/***~~

## Additional Tools

### QGroundControl(QGC) [Releases](https://github.com/mavlink/qgroundcontrol/releases)

> Ubuntu

* Install Dependencies

```bash
sudo usermod -a -G dialout $USER
sudo apt-get remove modemmanager -y
sudo apt install gstreamer1.0-plugins-bad gstreamer1.0-libav gstreamer1.0-gl -y
sudo apt install libqt5gui5 -y
```

Logout and login to make sure the change to user permissions

* Install QGC

Download AppImage from [GitHub releases](https://github.com/mavlink/qgroundcontrol/releases)

```bash
chmod +x ./QGroundControl.AppImage
./QGroundControl.AppImage # or double click the file
```
