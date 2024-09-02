JavaFXOS
==========

JavaFXOS is a Raspberry Pi distribution that boots directly into a JavaFX application. JavaFX is a best choice for embedded systems. It is a modern, fast, and feature-rich GUI toolkit. JavaFX provides easy and fast ways to create a modern user interface for your Raspberry Pi project. This distribution is designed to make it easy to run JavaFX applications on a Raspberry Pi without the need for a desktop environment.

![JavaFXOS logo](https://raw.githubusercontent.com/firatkiral/javafxos/main/media/javafxos.jpg)

![JavaFX ensemble app](https://raw.githubusercontent.com/firatkiral/javafxos/main/media/ensemble.gif)

A [`Raspberry Pi`](http://www.raspberrypi.org/) distribution to display JavaFX application in fullscreen. It includes JavaFX out of the box and the scripts necessary to load it at boot.

This repository contains the source script to generate the distribution out of an existing [`Raspbian`](http://www.raspbian.org) distro image.


Installation
--------------

* Download image from the [releases page.](https://github.com/firatkiral/javafxos/releases)
* Unzip the image and install it to an SD card [`like any other Raspberry Pi image`](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)
* It boots to a demo app if nothing is configured. You can replace the demo app with your own JavaFX app by following the steps below.
* Add your jfx application ``your-app.jar`` to ``javafxos`` folder in the first partition of the flashed card when using it like a flash drive. Configure ``launch.txt`` to point your javafx app, so it will be launched at boot.
* Configure your WiFi by editing ``javafxos-wpa-supplicant.txt`` if needed.
* Boot the Pi from the SD card
* Log into your Pi via SSH (it is located at [``javafxos.local`` `if your computer supports bonjour`](https://learn.adafruit.com/bonjour-zeroconf-networking-for-windows-and-linux/overview) or the IP address assigned by your router), default username is "pi", default password is "12345" and change the password using the ``passwd`` command.

Requirements
------------
* Raspberry Pi Zero 2 W or newer


Features
--------

* Loads JavaFX app at boot in fullscreen without the need for a desktop environment.

Developing
----------


Build JavaFXOS From Raspbian, Debian, or Ubuntu
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can build it by running the following commands:

    sudo apt-get update -y && sudo apt-get upgrade -y
    sudo apt install coreutils p7zip-full qemu-user-static jq git
    
    git clone https://github.com/guysoft/CustomPiOS.git
    git clone https://github.com/firatkiral/javafxos.git
    cd javafxos/src/image
    wget -c --trust-server-names 'https://downloads.raspberrypi.org/raspios_lite_armhf_latest'
    cd ..
    ../../CustomPiOS/src/update-custompios-paths
    sudo modprobe loop
    sudo bash -x ./build_dist

The final image will be created in ``src/workspace``. Follow the installation steps by using this image.