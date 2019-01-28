# Internet-in-a-Box (IIAB) Platforms

## Operating Systems

Install a **minimal** 64-bit OS in all cases, OLPC laptops notwithstanding!

Read the [partition scheme](https://github.com/iiab/iiab/wiki/IIAB-Platforms#disk-partitioning) below.

[FAQ.IIAB.IO](http://FAQ.IIAB.IO) documents [OS implementation trends](http://FAQ.IIAB.IO#What_OS_should_I_use.3F), among these recommended choices:

* [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) on Raspberry Pi 3, or 3 B+ _(WARNING: NOOBS IS NOT SUPPORTED, as its partitioning is very different!)_
* [Ubuntu 18.04](http://releases.ubuntu.com/18.04/) LTS _(WARNING: some versions of Ubuntu Server 18.04.1 from 2018-07-25 / 2018-07-26 contained a [very serious bug](https://github.com/iiab/iiab/wiki/IIAB-6.6-Release-Notes#known-issues))_
* [Debian 9.7](https://www.debian.org/releases/stretch/) "Stretch" LTS

The following OS's are theoretically possible, but may require extensive babysitting to get right:
* [Debian 10](https://www.debian.org/devel/debian-installer/) "Buster" prereleases ([quasi-daily ISO](https://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/), [weekly ISO](https://cdimage.debian.org/cdimage/weekly-builds/amd64/iso-cd/))
  * Install Tips: _PR [#1387](https://github.com/iiab/iiab/pull/1387)_
* [Debian "Sid"](https://wiki.debian.org/InstallFAQ#Q._How_do_I_install_.22unstable.22_.28.22sid.22.29.3F) for developers ([quasi-daily ISO](https://cdimage.debian.org/mirror/cdimage/daily-builds/sid_d-i/arch-latest/amd64/) seems to be the testing branch, not actually Sid/unstable branch)
* [Ubermix 4.x](http://wiki.ubermix.org/page/Ubermix_Changelog) based on Ubuntu 18.04
  * Create a USB stick (USB drive >= 4GB will suffice initially) to install Ubermix 4.x. Download the latest from http://ubermix.org/files.html and follow the instructions at http://ubermix.org/download.html
  * Read the "Customization Overview" section here: http://ubermix.org/customization.html. This is important information to understand.
  * Use your Ubermix USB install stick to do an ADVANCED install of Ubermix 4.x on your designated computer (turn off UEFI in its BIOS if possible) following the instructions under "Installing on your System" here: http://ubermix.org/download.html
    * You need to shrink the /home partition to make room for content to be stored in /library.  Change partition sizes by selecting Option 2 ("Advanced image") to set a larger size for the Default System partition (/dev/ext2) and/or larger size for the User Changes partition (/dev/ext3). You will be prompted to manually enter in partition sizes.
      * e.g. for an 80GB hard drive, consider 12GB (default) for the Default System partition and 50GB for the User Changes partition (IF /library IIAB content will be stored in the User Changes partition, wiped during factory reset reverts). You can adjust the partition sizes as necessary based on your hard drive size and content size needs.
      * e.g. consider reversing this: 50GB for the Default System partition and 12GB for the User Changes partition (IF /library IIAB content will be stored in the Default System partition, to protect it from factory reset reverts)
    * Ubermix will install in ~5 or so minutes.
  * Once Ubermix is installed and you are logged in, confirm the partitions are as you expect by opening up the Terminal and entering "df -h". Proceed if all is as expected. 
  * Turn off aufs (UnionFS). Follow steps #2-6 under the "Rebuilding the Base Image" section here: http://ubermix.org/customization.html 
  * Congratulations, you are now ready to install IIAB.
  * Install curl, by manually running: sudo apt install curl
  * Run IIAB's 1-line installer: http://d.iiab.io/6.7
  * Turn aufs (UnionFS) back on.
  * Consider building a USB stick to install everything at once onto other laptops/desktops, reading "Rebuilding the Base Image" in http://www.ubermix.org/customization.html ("5. Expert Options", then "1. Update the image on the key using this machine as a model")
* [CentOS 7.6](https://www.centos.org/download/) LTS
* [Ubuntu 16.04](http://releases.ubuntu.com/16.04/) LTS
* [Debian 8.11](https://www.debian.org/releases/jessie/debian-installer/) "Jessie" LTS
* [Fedora 18 (32-bit)](http://wiki.laptop.org/go/Releases) for legacy support of One Laptop per Child's (OLPC) XO laptops

_[Contact us if you can help, testing would be greatly appreciated!](http://FAQ.IIAB.IO#What_are_the_best_places_for_community_support.3F)_

## Hardware Platforms

Theoretically IIAB should run on any machine that can run Debian 9 or CentOS 7, and close derivatives.

In practice, IIAB has been tested on the platforms and configurations below.  For more detail, see ["What hardware should I use?"](http://FAQ.IIAB.IO#What_hardware_should_I_use.3F) within our [FAQ.IIAB.IO](http://FAQ.IIAB.IO).

#### Intel NUC and Gigabyte BRIX

Mini PC's also include MSI and Zotac etc, typically configured with 4 to 8 GB RAM and a 1TB of internal hard disk, or 200+ GB SSD. Most models have a minimum of four USB ports and some have an internal Wi-Fi adapter.

- Installs with Ubuntu 18.04 LTS, Debian 9.5 or CentOS 7.5

#### OLPC XO-1.5, XO-1.75, XO-4

OLPC laptops with an SD card of 32, 64, or 128 GB and a subset of the content found on machines with more storage or with an external hard drive.

- Only Fedora 18 has been tested, arising from OLPC OS

#### Raspberry Pi 3 or 3 B+

1 GB RAM, typically with a microSD card of 32, 64, or 128 GB.  Four USB ports allow the addition of Ethernet dongles, a Wi-Fi adapter, and possibly additional storage.

- Tested with Raspbian especially

(After building your Internet-in-a-Box microSD inside a Raspberry Pi 3 or 3 B+, also consider testing it within the amazing/tiny 512MB Raspberry Pi Zero W, available for [as little as $3.14 at Micro Center](http://www.microcenter.com/product/486575/zero_w) stores in the USA.)

#### VirtualBox VM

Virtual machines with varying configurations, especially Debian and CentOS 7, are often used for testing or proof-of-concept.

#### Other Recent Intel/AMD Computers

A number of users have successfully deployed IIAB on late model desktop and laptop computers.

## Disk Partitioning

Disable UEFI in your computer's BIOS if possible!

It's critical to avoid a large /home partition, so there's room to add content (in /library).  Pay close attention while installing your OS (Ubuntu, Debian etc).  You should remove (or dramatically shrink) this /home partition, if your Linux distro insists on creating one.

On a 1TB disk, we recommend the following 2-to-4 partitions, such as: (traditionally we use standard partitioning, but now increasingly LVM partitioning is also possible)
* /boot - 500 MB
* swap - 2 GB (optional partition, set this to your RAM size, or create a swap file if you prefer)
* / - 50 GB
* /library - the remainder (optional partition, can protect your content during major upgrades)

_On smaller disks and SD cards we recommend reducing (or eliminating) the swap partition, and avoiding the separate /library partition altogether._

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