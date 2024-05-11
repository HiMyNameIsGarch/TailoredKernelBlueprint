# Tailored Kernel Blueprint
I've always wanted to compile and customize my own kernel so one day I have
decided to do it. I've been using Linux for a long time and I've always been
keen on learning how things work under the hood. I use Artix btw and in this
project I will document my journey of compiling a custom kernel for my system.

# Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Configuring the Kernel](#configuring-the-kernel)
- [My Configuration] (#my-configuration)
- [Performance Tuning](#performance-tuning)
- [Compiling the Kernel](#compiling-the-kernel)
- [Installing the Kernel](#installing-the-kernel)
- [Configuring the Bootloader](#configuring-the-bootloader)
- [Conclusion](#conclusion)

# Introduction
The Linux kernel is the core of the operating system. It is responsible for
managing hardware resources, scheduling processes, and providing a system call
interface for user-space programs. The kernel is a complex piece of software
that is constantly being updated and improved by a large community of
developers.

Compiling a custom kernel allows you to tailor the kernel to your specific
needs. You can enable or disable features, optimize for performance, and remove
unnecessary code. This can result in a smaller, faster, and more secure kernel
that is better suited to your system.

# Prerequisites
Before you begin to tailor your beloved kernel you should to know your system
first, meaning you should run some commands in order to familiarize with your
architecture.

```
> lscpi
```
Here you can see the devices connected to your system.
```
> cat /proc/cpuinfo
```
Here you can see the information about your CPU.
```
> lsmod
```
Here you can see the modules that are currently loaded in your system.

# Getting Started
First of all you need to download the kernel source code. You can download the
latest stable release from the official website or clone the git repository.
I will be using the latest stable release for this project.
```
> wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.14.6.tar.xz
```

Next, you need to extract the source code and navigate to the kernel directory.
```
> tar -xvf linux-5.14.6.tar.xz && cd linux-5.14.6
```
Next you need to install the necessary tools to compile the kernel. You can
install the required packages using the package manager of your distribution.
```
> sudo pacman -S base-devel bc
```
We are almost there, now you need to configure the kernel.
Firstly you need to copy the default kernel configuration file
Now depending on your system you can use one of the following commands.
```
> cp /boot/config-$(uname -r) .config # For Debian/Ubuntu and other based systems
> zcat /proc/config.gz > .config # For Arch based systems
```

# Configuring the Kernel
Finally, we made it to the most important part of the project. Here you can
enable or disable features, optimize for performance, and remove unnecessary
code. Isn't this fun?
Also before starting the configuration you can run the following command to
launch the configuration menu.
```
> make oldconfig
```
As the docs says: it will "Update current config utilising a provided .config
as base"
Now we are ready to rock. You can run the following command to start the
configuration menu.
```
> make menuconfig
```

# My Configuration
I will be sharing my configuration here, BUT I strongly recommend you to
configure the kernel according to your needs. You can find my configuration
file in the root of the project. <br>
Here I will just document the changes I made to the default configuration.

# Performance Tuning
I will be sharing some performance tuning tips here. You can apply these tips
to your configuration file.

