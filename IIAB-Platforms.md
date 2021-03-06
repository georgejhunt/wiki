# Internet-in-a-Box (IIAB) Platforms

## Operating Systems

Read the [partition scheme](https://github.com/iiab/iiab/wiki/IIAB-Platforms#disk-partitioning) below.

Please install a **minimal** OS if possible, as [IIAB's installer](http://download.iiab.io) will add the packages you need.

1) [FAQ.IIAB.IO](http://FAQ.IIAB.IO) documents Internet-in-a-Box (IIAB) [OS trends](http://FAQ.IIAB.IO#What_OS_should_I_use.3F), among these recommended choices:

   * [Raspbian Buster](https://www.raspberrypi.org/downloads/raspbian/) on Raspberry Pi 3, 3 B+ or 4 _(WARNING: NOOBS IS NOT SUPPORTED, as its partitioning is very different!)_
   * [Ubuntu 18.04](http://releases.ubuntu.com/18.04/) LTS on AMD64 _(WARNING: IIAB's [1-line installer](http://download.iiab.io) must be run as root!)_
   * [Debian 10](https://www.debian.org/releases/buster/) "Buster" LTS on AMD64 ([installer](https://www.debian.org/releases/buster/debian-installer/), [#1387 install tips](https://github.com/iiab/iiab/issues/1387))

2) The following OS's are theoretically possible, but may require extensive babysitting to get right:

   * [Ubuntu 20.04](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule) LTS (Focal Fossa) daily pre-releases: [Desktop](http://cdimage.ubuntu.com/daily-live/pending/) or [Server](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/).  Install Tips:
     * On Raspberry Pi, try the latest `arm64` pre-release from http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/ and for now install Node.js 10.x manually using `apt install nodejs npm`, then upgrade it to Node.js 12.x using https://linuxconfig.org/how-to-install-node-js-on-ubuntu-20-04-lts-focal-fossa, then add the line `nodejs_installed: True` to the end of file `/etc/iiab/iiab_state.yml` (creating the file if necessary!)
     * KA Lite fails to install on Ubuntu 20.04 pre-release (arm64): "You are running Setuptools on Python 2, which is no longer supported" "ensure you are installing Setuptools using pip 9.x or later or pin to 'setuptools<45'": [#2312](https://github.com/iiab/iiab/issues/2312)
     * Unable to install Calibre-Web on Ubuntu 20.04 pre-release: Python 3.8 / pip3 issue?  A workaround is available at: [#2311](https://github.com/iiab/iiab/issues/2311)
   * [Ubuntu Server 19.10.1 for Raspberry Pi](https://ubuntu.com/download/raspberry-pi) released 2019-12-05 ([docs](https://wiki.ubuntu.com/ARM/RaspberryPi), [downloads](http://cdimage.ubuntu.com/releases/19.10.1/release/)).  Stick with the 32-bit version for now, until 64-bit Kiwix support appears ([kiwix/kiwix-build#396](https://github.com/kiwix/kiwix-build/issues/396)).  Please do not install or enable Sugarizer in /etc/iiab/local_vars.yml as this OS lacks MongoDB.
   * [Ubuntu 19.10](http://releases.ubuntu.com/19.10/) Eoan Ermine:
     * [Server & Desktop editions for AMD64](http://cdimage.ubuntu.com/releases/19.10/release/), released 2019-10-17 <!--([server](http://cdimage.ubuntu.com/ubuntu-server/daily/current/) or [desktop](http://cdimage.ubuntu.com/daily-live/current/))-->
       * Install Tips: _[#2003](https://github.com/iiab/iiab/issues/2003)_
   * [Debian "Sid"](https://wiki.debian.org/DebianUnstable) for developers
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
     * Run IIAB's 1-line installer: http://d.iiab.io
     * Turn aufs (UnionFS) back on.
     * Consider building a USB stick to install everything at once onto other laptops/desktops, reading "Rebuilding the Base Image" in http://www.ubermix.org/customization.html ("5. Expert Options", then "1. Update the image on the key using this machine as a model")

3) The following OS's are **no longer recommended** at this time:

   * [Debian 9.x](https://www.debian.org/releases/stretch/) "Stretch" LTS
   * [CentOS 7.7](https://www.centos.org/download/) LTS
   * [Ubuntu 16.04](http://releases.ubuntu.com/16.04/) LTS
   * [Debian 8.11](https://www.debian.org/releases/jessie/debian-installer/) "Jessie" LTS
   * [Fedora 18 (32-bit)](http://wiki.laptop.org/go/Releases) for legacy support of One Laptop per Child's (OLPC) XO laptops

_**[Contact us](http://FAQ.IIAB.IO#What_are_the_best_places_for_community_support.3F) if you can help, as [user-driven testing & co-design are greatly appreciated,](http://internet-in-a-box.org/pages/contributing.html) strengthening everyone's community product!**_

## Hardware Platforms

Theoretically IIAB should run on any machine that can run Ubuntu, Debian or close derivatives (like Raspbian, Ubermix, etc).  CentOS 7 and Fedora are not nearly as well supported, as of February 2019 ([#1434](https://github.com/iiab/iiab/issues/1434)).

In practice, IIAB has been tested on the platforms and configurations below.  For more detail, see ["What hardware should I use?"](http://FAQ.IIAB.IO#What_hardware_should_I_use.3F) within [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

#### Intel NUC and Gigabyte BRIX

Mini PC's also include MSI and Zotac etc, typically configured with 4 to 8 GB RAM and a 1TB internal hard disk, or 200+ GB SSD.  Most models have a minimum of four USB ports and some have an internal Wi-Fi adapter.

- Install Ubuntu 18.04 LTS, or Debian 10 "Buster" <!--or CentOS 7.6-->

#### OLPC XO-1.5, XO-1.75, XO-4

OLPC laptops with an SD card of 32, 64, or 128 GB and a subset of the content found on machines with more storage or with an external hard drive.

- Only Fedora 18 has been tested, arising from [OLPC OS](http://wiki.laptop.org/go/Releases)

#### Raspberry Pi 3, 3 B+ or 4

1 GB RAM, typically with a microSD card of 32, 64, 128 or 256 GB.  Four USB ports optionally allow for Ethernet dongles, external Wi-Fi, and possibly additional storage.

- Use the Raspbian OS _(WARNING: NOOBS IS NOT SUPPORTED, as its partitioning is very different!)_

(After building your Internet-in-a-Box microSD inside a Raspberry Pi 3 or 3 B+, also consider testing it within the amazing/tiny 512MB Raspberry Pi Zero W, available for [as little as $3.14 at Micro Center](http://www.microcenter.com/product/486575/zero_w) stores in the USA.)

#### VirtualBox VM

Virtual machines with varying configurations, especially Ubuntu and Debian, are often used for testing and proofs-of-concept.

#### Other Recent Intel/AMD Computers

A number of users have successfully deployed IIAB on late model desktop and laptop computers.

## Disk Partitioning

Disable UEFI in your computer's BIOS if possible!

It's critical to avoid a large /home partition, so there's room to add content (in /library).  Pay close attention while installing your OS (Ubuntu, Debian etc).  You should remove (or dramatically shrink) this /home partition, if your Linux distro insists on creating one.

On a 1+ TB disk, we recommend the following 2-to-4 partitions, such as: (traditionally we use standard partitioning, but now increasingly LVM partitioning is also possible)
* /boot - 500 MB
* swap - 2 GB (optional partition, set this to your RAM size, or create a swap file if you prefer)
* / - 50 GB
* /library - the remainder (optional partition, can protect your content during major upgrades)

On smaller disks and SD cards, also consider:
1) reducing (or altogether eliminating) the swap partition &mdash; see variable `pi_swap_file_size` in [/etc/iiab/local_vars.yml](http://FAQ.IIAB.IO#What_is_local_vars.yml_and_how_do_I_customize_it.3F)
2) avoiding a separate partition for /library &mdash; far better to keep your content directory (/library) within the main partition!

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