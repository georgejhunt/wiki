# Internet-in-a-Box (IIAB) Platforms

## Operating Systems

Install a **minimal** 64-bit OS in all cases, OLPC laptops notwithstanding!

Read the [partition scheme](https://github.com/iiab/iiab/wiki/IIAB-Platforms#disk-partitioning) below.

[FAQ.IIAB.IO](http://wiki.laptop.org/go/IIAB/FAQ) documents [OS implementation trends](http://wiki.laptop.org/go/IIAB/FAQ#What_OS_should_I_use.3F), among these recommended choices:

* [Raspbian Stretch with Desktop (GUI) or Lite (headless)](https://www.raspberrypi.org/downloads/raspbian/) on Raspberry Pi 2 or 3
* [Ubuntu 16.04](http://releases.ubuntu.com/16.04/) LTS
* [Debian 9.2](https://www.debian.org/releases/stretch/) or [9.2.1](http://cdimage.debian.org/debian-cd/9.2.1/) "Stretch" LTS
* [CentOS 7.4](https://www.centos.org/download/) LTS

The following OS's are theoretically possible, but require extensive babysitting to get right:

* [Debian 8.9](https://www.debian.org/releases/jessie/debian-installer/) "Jessie" LTS
* [Fedora 18 (32-bit)](http://wiki.laptop.org/go/Releases) for legacy support of One Laptop per Child's (OLPC) XO laptops

_[Contact us if you can help, testing would be greatly appreciated!](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_best_places_for_community_support.3F)_

## Hardware Platforms

Theoretically IIAB should run on any machine that can run Debian 9 or CentOS 7, and close derivatives.

In practice, IIAB has been tested on the platforms and configurations below.  For more detail, see ["What hardware should I use?"](http://wiki.laptop.org/go/IIAB/FAQ#What_hardware_should_I_use.3F) within our [FAQ.IIAB.IO](http://wiki.laptop.org/go/IIAB/FAQ).

#### Intel NUC and Gigabyte BRIX

Mini PC's also include MSI and Zotac etc, typically configured with 4 to 8 GB RAM and a 1TB of internal hard disk, or 200+ GB SSD. Most models have a minimum of four USB ports and some have an internal Wi-Fi adapter.

- Installs with Ubuntu 16.04 LTS, Debian 9.1 or CentOS 7.4

#### OLPC XO-1.5, XO-1.75, XO-4

OLPC laptops with an SD card of 32, 64, or 128 GB and a subset of the content found on machines with more storage or with an external hard drive.

- Only Fedora 18 has been tested, arising from OLPC OS

#### Raspberry Pi 2 and 3

1 GB RAM with a microSD card of 32, 64, or 128 GB.  Four USB ports allow the addition of Ethernet dongles, a Wi-Fi adapter, and possibly additional storage.

- Tested with Raspbian especially

#### VirtualBox VM

Virtual machines with varying configurations, especially Debian and CentOS 7, are often used for testing or proof of concept.

#### Other Recent Intel/AMD Computers

A number of users have successfully deployed IIAB on late model desktop and laptop computers.

## Disk Partitioning

For large disks we recommend the following partitions: (traditionally we use standard partitioning, but now increasingly LVM partitioning is also possible)
* /boot - 500 MB
* swap - 2 GB
* / - 50 GB
* /library - the remainder

For smaller disks and SD cards we recommend not creating a separate /library partition and reducing (or eliminating) swap.

Please note that installers for Fedora and CentOS often put the remaining disk space into /home.  You will need to remove this partition and create /library.  This can be done through the graphical installer that comes with Fedora.

## Network Adapters

Each of the above devices may have one or more network adapters.  These may be internal Ethernet, internal or external Wi-Fi, or Ethernet dongles.  The role the server is able to play in the [network](https://github.com/iiab/iiab/wiki/IIAB-Networking) will depend on what adapters and connections it has.

#### Sample Gateway Configurations

* WAN on internal Wi-Fi and LAN on internal Ethernet
* WAN on internal Ethernet and LAN on internal or external Wi-Fi as Access Point
* WAN on Ethernet dongle and LAN on internal Ethernet with optional bridged internal/external Wi-Fi as Access Point

#### Sample Appliance Configurations

* Internal Wi-Fi connected to an existing LAN
* Internal Ethernet connected to an existing LAN
* Ethernet dongle connected to an existing LAN