# Installing Internet-in-a-Box (IIAB)

## Quick Links

* [Overview](#overview)
* [Expert Mode](#expert-mode)
* [Install the Software](#install-the-software)
    * [Do Everything from Scratch](#do-everything-from-scratch)
    * [Take a Short Cut](#take-a-short-cut)
* [Configure the Server](#configure-the-server)
    * [Server Security](#server-security)
    * [Configure Menu](#configure-menu)
    * [Supported Network Modes](#supported-network-modes)
    * [Enable Services](#enable-services)
* [Add Content](#add-content)
    * [ZIM Files](#zim-files)
    * [RACHEL](#rachel)
    * [KA Lite (for Khan Academy)](#ka-lite-for-khan-academy)
    * [Copy KA Lite Videos Manually](#copy-ka-lite-videos)
    * [OpenStreetMap](#openstreetmap)
    * [Local Content](#local-content)
    * [External USB/Drive Content](#external-usbdrive-content)

## Overview

Setting up a working IIAB server requires actions grouped into roughly three areas:

* Install the Software
* Configure the Server - Set Parameters and Enable Services
* Add Content

## Expert Mode

This is for people who already know how to do everything in these instructions and enjoy doing them multiple times by missing the nuances that make this install different from things they have done before. **If you are an expert, at least read about [PARTITIONING](https://github.com/iiab/iiab/wiki/IIAB-Platforms#disk-partitioning) as so many miss this part.**  Reading about [networking](https://github.com/iiab/iiab/wiki/IIAB-Networking) will probably come in handy as well.

## Install the Software

There are basically two ways to install IIAB software:

   1. Do everything from scratch.  Strongly recommended (since IIAB 6.4 especially) as our new [1-line installer](http://download.iiab.io/6.5/rpi) scripts do essentially everything!
   2. Take a short cut by getting files from someone else who did everything from scratch or at least some of the steps.  Here are some [suggestions](http://tinyurl.com/iiabimages) on how to create short cut image files, towards helping others.

The _advantage_ of doing everything from scratch is that you will get exactly what you want and you will get the latest version of the software.  The _disadvantage_ is that it is more work.

The _advantage_ of a short cut is that it will usually take less time and effort.  The _disadvantage_ is that there may not be files available for every platform and every configuration and the files may be out of date.

### Do Everything from Scratch

Here is the complete list of the steps required. Some may already be done.

1. Assemble your hardware with your chosen amount of [RAM, storage, and network devices](http://wiki.laptop.org/go/IIAB/FAQ#What_hardware_should_I_use.3F).  See [IIAB Platforms](https://github.com/iiab/iiab/wiki/IIAB-Platforms#disk-partitioning) for the **partitioning scheme** and [IIAB Networking](https://github.com/iiab/iiab/wiki/IIAB-Networking) overview.

   **Traditionally we use Standard partitioning, but increasingly in 2017 LVM partitioning is possible as well. In any case, the above "IIAB Platforms" document is the place to start for all partitioning tips.**

2. Install your OS (e.g. [Ubuntu 16.04 LTS](http://releases.ubuntu.com/16.04/)) using a **minimal** install (do install ssh, but avoid installing Apache or most anything else!)  If using a Raspberry Pi 3, install the [Raspbian OS](https://www.raspberrypi.org/downloads/raspbian/) ("Lite" headless version or "With Desktop" graphical version) onto a microSD.  If installing onto XO laptops, use [OLPC's latest OS](http://wiki.laptop.org/go/Releases) (based on Fedora 18).  See more at [IIAB Platforms](https://github.com/iiab/iiab/wiki/IIAB-Platforms) and in our [FAQ](http://wiki.laptop.org/go/IIAB/FAQ#What_OS_should_I_use.3F).  _WARNING: OTHER LINUX DISTRIBUTIONS MAY NOT/YET WORK!_

3. While installing over Wi-Fi is possible, an Ethernet (live Internet) cable is **strongly recommended** during installation!  In any case, log into your machine with an attached monitor/keyboard or via ssh.  Verify your Internet connection by typing:
```
   ping mit.edu
```
4. Escalate to root using "sudo su -" or similar.

5. _**Ansible 2.4.1+ is required on all OS's** so that ./iiab-install (formerly "./runansible") can run efficiently and incrementally.  Run "ansible --version" to make sure you don't have an older version of Ansible installed.  If you do, run "apt purge ansible" or "pip uninstall ansible" (depending how you originally installed Ansible, see [#375](https://github.com/iiab/iiab/issues/375#issuecomment-334500152) & [#564](https://github.com/iiab/iiab/issues/564#issuecomment-347264985)) prior to Ansible 2.4.x's installation below._

6. On Raspbian, Ubuntu or Debian doing everything from scratch involves a few simple steps:
```
   apt update
   apt -y dist-upgrade
   apt -y clean

   apt -y install git

   mkdir -p /opt/iiab
   cd /opt/iiab/
   git clone https://github.com/iiab/iiab --depth 1
   git clone https://github.com/iiab/iiab-admin-console --depth 1
   git clone https://github.com/iiab/iiab-menu --depth 1
   git clone https://github.com/iiab/iiab-factory --depth 1

   cd /opt/iiab/iiab/vars/
   wget http://download.iiab.io/6.5/rpi/local_vars.yml
   # Above assumes a virgin system (wget WON'T overwrite existing files)

   # In general please examine local_vars.yml carefully (and modify as nec)
   # before running Ansible (below, which can take 1-2 hours the 1st time!)

   # NOTE: you can change many/most settings after install too, using the
   # Admin Console (http://box/admin) as documented at: http://FAQ.IIAB.IO

   cd /opt/iiab/iiab/scripts/
   ./ansible
   # Installs Ansible 2.4.x+ from PPA

   cd /opt/iiab/iiab/
   ./iiab-install
   # TRY TO RERUN THE ABOVE LINE IF IT FAILS (if networking glitches etc?)

   cd /opt/iiab/iiab-admin-console/
   ./install
   # Installs Admin Console; runs iiab-get-kiwix-cat to d/l Kiwix catalog

   cd /opt/iiab/iiab-menu/
   ./cp-menus
   # Installs Dynamic Menuing for /library/www/html/home/index.html
```
The above happens automatically if you run this 1-line installer, which includes [~12 server apps](http://wiki.laptop.org/go/IIAB/local_vars.yml):
```
   curl download.iiab.io/6.5/rpi/load.txt | sudo bash
```
_These 1-line installers require the latest Raspbian OS (on Raspberry Pi 3), Ubuntu 16.04 LTS (on x86_64 PC's) or Debian 9.x (on x86_64 PC's)._  Note the above can take 2 hours on a Raspberry Pi &mdash; even with a fast Internet connection &mdash; so if you want a faster installer, instead try this one below, with just [~6 server apps](http://wiki.laptop.org/go/IIAB/local_vars_min.yml):
```
   curl download.iiab.io/6.5/rpi/load-min.txt | sudo bash
```
Conversely a much larger but slower installation is possible, if you want to experiment with a more full suite of [~20 servers apps](http://wiki.laptop.org/go/IIAB/local_vars_big.yml):
```
   curl download.iiab.io/6.5/rpi/load-big.txt | sudo bash
```
Please browse the above URLs to inspect and learn from the automated steps of the installation process, and do write to bugs @ iiab.io if you find issues, Thank You !

_In general, beware that ./iiab-install (formerly "./runansible") runs slowly (1) the 1st time you run it (2) if you permit your Raspberry Pi 3 CPU to rise above 80C on a hot day without active ventilation (3) if you're using a slower/older SD card and/or (4) if you have a slow Internet connection._

_Whereas subsequent runs (e.g. via Admin Console -> Configure -> Install Configured Options) can take as little as 15-to-25 minutes on the Raspberry Pi 3._

Similarly, if you want to help test CentOS, please do help us [improve on](https://github.com/iiab/iiab/issues/89) these 2 much older recipes from earlier in 2017:
```
   http://download.iiab.io/6.2/x86/centos-load.txt
   https://github.com/iiab/iiab-factory/blob/master/curl-me
```
As explained in the above "curl" scripts, a reboot is generally necessary before IIAB becomes fully functional, e.g. to put Hostname change into effect, etc.

**Please note that if you need to upgrade from a recent version, and it has been some time since you cloned IIAB, you may want to consider the following instead of a fresh install:** _(upgrades are at your own risk)_
```
   cd /opt/iiab/iiab/
   git pull
   ./iiab-install --reinstall
```
Also recommended: On Raspbian, Ubuntu or Debian, download and install the latest security/package revisions by running `apt update` followed by `apt dist-upgrade` (might upgrade your kernel) per the recommendations at http://wiki.laptop.org/go/IIAB/Security (on CentOS, run `yum update` and on more recent versions of Fedora run `dnf upgrade`).

**Please note that if SELinux was enabled it will be disabled and the server will reboot at the end of the install.  In that case the server may get a new IP address, usually one higher than the previous one. The server may also disconnect during the install in which case you will need to reconnect in order to continue.**

You can see the log of the last install by typing:
```
   more /opt/iiab/iiab/iiab-install.log
```
**Proceed to [Configure the Server](#configure-the-server).**

### Take a Short Cut

This step applies if you've been given a pre-built disk image (ISO file or similar) for a particular configuration and even content i.e. if everything from the steps listed above has already been completed for you!

In general the process of using one of these files is to download it to a separate computer and then write it to storage media for the target machine. What happens next depends on the specific file downloaded.

You will need tools to decompress these files and write them to storage.  On Linux and MacOS these tools will already likely be there. On Windows you will need to download them.

#### Tools

* Linux or MacOS - dd, unzip, xz

* Windows - download:
    * Win32 Disk Imager from https://sourceforge.net/projects/win32diskimager/
    * 7-Zip from http://www.7-zip.org
    * Optionally FileZilla from https://filezilla-project.org

Naturally, while the everything-from-scratch steps are generic and apply to any platform, short cuts are for a specific platform.

Instructions for specific platforms follow.

#### Raspberry Pi 3

Raspberry Pi 2 should also work, but is slower, and lacks the all-important internal Wi-Fi!

The most recent IIAB for Raspian Lite (or for the full Raspbian with Desktop, including X Windows and desktop apps) can be installed from http://download.iiab.io

There is also a README with instructions.

You can also have a look at:

       https://www.raspberrypi.org/documentation/installation/installing-images/

Please ignore everything down to **WRITING AN IMAGE TO THE SD CARD** (we support Raspbian but not NOOBS!)

#### Mini PC's like Intel NUC and Gigabyte BRIX

Note that most Intel NUCs (Next Unit of Computing) shipping since 2015, including the 5th and 6th generation Intel NUC's, have a soldered-in Wi-Fi chip limited to 12 clients maximum. Its competitor the Gigabyte BRIX suffers from the same limitation out of the box (factory units arrive with an Intel Wi-Fi module) but thankfully this Wi-Fi module is removable! Specifically, the Gigabyte BRIX's Wi-Fi socket has been tested to accept less-constrained Wi-Fi cards, such as Atheros modules available for less than $10.

If you are given a pre-built x86 image, it should generally install via Clonezilla when booted on the target machine.

The image (ending in .img) should be written to a USB stick using the same software as for Raspberry Pi and OLPC XO laptops.

Note that these images will write two partitions to a USB stick (thumb drive).  The first partition contains the Clonezilla tool, which uses the data from the second partition to initialize your hard disk.

Finally, while these images have been developed on the Intel NUC, they may well work on other Intel machines too (do let us know!)

#### Installation on OLPC XO laptops is not currently supported on release-6.2+, due to lack of time to test the following general strategy:

* Install [OLPC OS 13.2.8](http://wiki.laptop.org/go/Release_notes/13.2.8) or similar onto the XO laptop
* In ``My Settings -> Power`` turn off Automatic Power Management
* Connect all the network interfaces and reboot
* Install git and Ansible: (for dependencies)

         su -
         git clone https://github.com/ansible/ansible --branch stable-2.2 --recursive
         cd ansible
         python setup.py install

  Earlier in 2017 Ansible 2.2.0 had been required, avoiding 2.2.1 which had issues.

  _As of October 2017, Ansible 2.4.x is required &mdash; please verify Ansible's version number with:_

         ansible --version

* Clone the IIAB git repo, and cd into it:

         mkdir -p /opt/iiab
         cd /opt/iiab/
         git clone --branch release-6.2 --depth 1 https://github.com/iiab/iiab
         cd /opt/iiab/iiab/

* Verify all the network interfaces are visible and have the correct interface label:

         ip addr            (similar to legacy command "ifconfig")

* Optionally, verify that all network interfaces are properly autodetected:

         bash roles/common/library/iiab_facts

* From the iiab directory, run initial setup.  The XO will automatically reboot early in the install and must be restarted with "./iiab-install (formerly "./runansible") to complete the install process: (increases size of /tmp so installs will complete successfully)

        ./iiab-install        (formerly "./runansible", try to rerun this if it fails!)

## Configure the Server

At this point you should be able to connect to [http://box](http://box) from a browser.  In certain cases http://box.lan, http://schoolserver.lan, http://localhost or http://172.18.96.1 may instead be necessary.

To begin configuring the server, connect to its Admin Console at [http://box/admin](http://box/admin) (username: **iiab-admin** password: **g0adm1n** -- note the numbers 0, 1).  In general, all default/initial passwords are documented at "What are the default passwords?" within: http://FAQ.IIAB.IO

This permits selection of options, services, languages, etc to permit additional services, and educational resources to be enabled and selected for download.

Please click on the **Help** link to get detailed information on configuration options.

### Server Security

The first time you sign into the Admin Console would be the best time to change the password.  Select the Utilities menu option and the first item, change password.  Fill in the form and click Change Password.

Please also read about and take seriously [Internet-in-a-Box security practices](http://wiki.iiab.io/Security).

### Configure Menu

Once the password has been set you should start with the Configure menu item.  The overall process is:

1. Select each sub-menu item and enter any desired parameters.  **Help** is available for each screen and parameter.
2. Click **Save Configuration**
3. Click **Install Configured Options** 
4. Monitor the progress of the Configuration job in Utilities -> Display Job Status.
5. ***Note*** that after Display Job Status shows "Success", it may be necessary to reboot, to enable all the selected changes.

This job can take a substantial amount of time depending on the capacity of the platform involved and how much of the software was included in the initial image.

At this point you are ready to proceed to [Add Content](#add-content).

### Supported Network Modes

Operator can select one of [three modes of operation](https://github.com/iiab/iiab/wiki/IIAB-Networking):

   * **Appliance** - No firewall, no dhpcd, no DNS, just a contributor to an already existing network.
   * **Gateway** - Does dhcpd (IP addresses), name lookup (DNS), firewall, local web page cache for faster retrieval the second time, content filtering to reduce porn (DansGuardian), and site "whitelists" if wanted.
   * **LAN Controller** (Local Area Network) - In this mode, the server configures clients with IP addresses (dhcpd - dynamic host configuration protocol), name resolution (defines "box" and "schoolserver" for all clients, etc).

Based upon selection of the above mode in the Admin Console, the IIAB software will attempt to set up network connections. If "Appliance" mode is wanted, the network adapter will be set up. If "Gateway" is selected, and one of the adapters discovers that it is connected to a source of IP addresses, that adapter will be the internet, and the other the Wi-Fi connector. If "LAN Controller" is selected, any adapter found will be act as server to any clients that might ask to connect.

The IIAB installation attempts to determine the network topology based on the number and types of connections it discovers. In general, it looks to see if there is a connection to a gateway and whether other wireless or wired connections are present.

### Enable Services

Different services (a.k.a. server apps) can be enabled on your IIAB server by checking boxes in http://box/admin -> Configure menu -> Enable Services.

Then click Save Configuration -> Install Configured Options.

Finally, confirm that it has completed in the coming minutes, within Utilities menu -> Display Job Status.

## Add Content

Since IIAB/XSCE 6.0, many kinds of content (but not all) can be downloaded and installed through your Internet-in-a-Box server's Admin Console (http://box.lan/admin).

WARNING: some of these Content Packs are quite large and you should pay attention to the space available and space required displayed on each screen.  Note that space calculations may not reflect multiple types of downloads happening simultaneously.

### Add with Admin Console

To begin, [log in](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_default_passwords.3F) to the Admin Console (http://box.lan/admin), take the **Install Content** menu item, and view relevant **Help**.

#### ZIM Files

ZIM files (ZIMs) are compressed and indexed (rapidly searchable) Content Packs prepared by http://kiwix.org.  They include Wikipedia, Wiktionary, TED Talks, and many other educational/reference materials in multiple languages.  Download and install these as follows:

1. Within Admin Console -> Install Content, hit button **Refresh Kiwix Catalog** to update your list of available ZIMs with the very latest from Kiwix.org.

2. Within Install Content, take menu option **Get ZIM Files from Kiwix**.  Before making your selection of ZIM Content Packs, use buttons Select Languages -> More Languages to be sure you're viewing all relevant choices, in many more languages than just {English, Spanish, French, Portuguese, Arabic and Hindi}.

3. Carefully finalize your selection of ZIM Content Packs, among the many choices.  _Avoid downloading/installing more than 10 at once!_

4. Hit button **Install Selected ZIMs** to begin downloading and installing them onto your server.  _This can take a very long time, during which time your server may appear unresponsive (within the first hour especially) while it's working!_

5. Monitor progress within Admin Console -> Utilities -> **Display Job Status**.  Each ZIM spawns 3 jobs which (1) download, (2) unzip, then (3) move the pieces into position within /library/zims/content and /library/zims/index.  In the past, after installing ZIMs, you also needed to run "iiab-make-kiwix-lib; systemctl restart kiwix-serve" &mdash; but this is no longer necessary as of IIAB/XSCE 6.2.

WARNING: there are certain situations (particularly if you've removed a ZIM from /library/zims, e.g. to clean house or when a malformed ZIM failed to install its index) where you need to run Admin Console -> Install Content -> **Refresh ZIMs Installed List**.  This will fix the listing within the above "Get ZIM Files from Kiwix" downloader, so it correctly shows which ZIMs you truly have installed (and which others are truly downloadable!)

#### KA Lite (for Khan Academy)

KA Lite is the most popular platform to experience Khan Academy videos, and a huge collection of associated exercises.  Accounts may be created for students and teachers if you choose to use KA Lite's LMS functionality as well, to track your own progress (or others').

To download the Khan Academy videos of your choosing, in various languages, use KA Lite's downloader available in these places:

* Admin Console -> Install Content -> Download Khan Academy Videos -> Launch KA Lite
* [http://box:8008](http://box:8008) (or [http://box.lan:8008](http://box.lan:8008) on non-standard devices/browsers)
* [http://172.18.96.1:8008](http://172.18.96.1:8008) on much older devices/browsers

Username/password is Admin/changeme [upon installation](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_default_passwords.3F).

KA Lite's English exercises and subtitles (about 1 GB) MUST be downloaded and installed, even if you are not using English videos, starting with KA Lite 0.17.0 early in 2017.  Thankfully our [IIAB load scripts on Raspberry Pi](http://download.iiab.io/6.5/rpi) include perform this essential piece for you.

See also ["KA Lite Administration: What tips & tricks exist?"](http://wiki.laptop.org/go/IIAB/FAQ#KA_Lite_Administration:_What_tips_.26_tricks_exist.3F) within [FAQ.IIAB.IO](http://FAQ.IIAB.IO).

### Add Content Manually

#### RACHEL

Download [RACHEL modules](http://dev.worldpossible.org/cgi/rachelmods.pl) manually using rsync, to `/library/www/html/modules`

After a module has been downloaded successfully (rerun rsync if there are connectivity issues) local/offline users can access it with URL:
```
   http://box/modules/<module-name>
```
#### Copy KA Lite Videos

If KA Lite videos have been obtained from another install or on some storage medium they can be copied directly to KA Lite without going through the admin interface.

1. Copy to /library/ka-lite/content/
2. Issue the command ``systemctl restart kalite-serve`` to restart the server

#### OpenStreetMap

[OpenStreetMap.org](http://OpenStreetMap.org) (OSM) is much like Google Maps, but more democratic and without advertising &mdash; anybody can change it, much like Wikipedia only for maps.

Internet-in-a-Box enables OSM to be viewable, zoomable and searchable while offline.

Currently in 2017, 16 levels of zoom are possible, from level 0 to 15.  This is about 110GB total, so you may need to [mail order a physical drive](http://wiki.laptop.org/go/IIAB/FAQ#What_can_I_do_with_E-books_and_Internet-in-a-Box.3F) from the volunteers at [unleashkids.org](http://unleashkids.org) if the levels posted to [download.iiab.io/content](http://download.iiab.io/content) are insufficient.

Either way, the following directories and their contents are needed:

* /library/knowledge/modules/geonames_index
* /library/knowledge/modules/openstreetmap

Implementers can reduce OSM's storage needs by eliminating high-zoom levels within directory openstreetmap, where each zoom level is contained within its own subdirectory.

Example 1: newer install images typically include layers 0 to 8 (140MB) fully working out-of-the-box, even prior to your customizing your own Internet-in-a-Box server.

Example 2: osm12.tar.gz from [download.iiab.io/content](http://download.iiab.io/content) includes layers 0 to 12 (8.2GB) showing many towns/rivers/parks worldwide, not just cities/countries/seas.

As you can see, each increasing zoom level generally requires exponentially ever larger amounts of storage!

_ASIDE: there is a very dedicated group of people coming together to improve the quality, compactness, vividness, searchability (and UX) of OpenStreetMap for the entire developing world in 2017.  Please do make contact with holt @ laptop.org if you too can help here._

#### Local Content

Schools/Clinics often have custom learning materials they want "permanently" shared with everyone on site. Such PDF's, DOC files, videos, images, audio recordings and HTML (etc!) can be copied to `/library/www/html/local_content` so that users can browse it, with a URL like [http://box/usb](http://box/usb) or [http://box.lan/usb](http://box.lan/usb)

#### External USB/Drive Content

For spontaneous (ad hoc) access to materials and teacher content (handouts, lessons, etc) these can be placed on a USB stick or drive, within a folder named:

* usb

...which will appear under URL [http://box/usb](http://box/usb) when teachers' sticks/drives are plugged into the server's USB ports.  Warning: some older phones/devices may require you to type in [http://box.lan/usb](http://box.lan/usb) or http://172.18.96.1/usb

For legacy support of the LibraryBox and PirateBox communities, teachers may also place shareable content in folder names {share, Share, Pirateshare/Share} on their USB sticks/drives.

Bonus: after the lesson, teachers should feel free to remove their USB sticks/drives without warning, as the IIAB server should unmount USB sticks/drives automagically.

See "[Can teachers display their own content?](http://wiki.laptop.org/go/IIAB/FAQ#Can_teachers_display_their_own_content.3F)" within our Frequently Asked Questions ([FAQ.IIAB.IO](http://FAQ.IIAB.IO)) for more info.