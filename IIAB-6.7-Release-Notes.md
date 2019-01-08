### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.7 will build on [IIAB 6.6](https://github.com/iiab/iiab/wiki/IIAB-6.6-Release-Notes), to be released in January 2019 ([Wiki](http://wiki.laptop.org/go/IIAB/6.7), [GitHub](https://github.com/iiab/iiab/milestone/4)) in service of DIY digital libraries everywhere.

Consider installing a pre-release today, from <a href=http://download.iiab.io/6.7/>download.iiab.io/6.7</a> !

### What's New? (TENTATIVE)

* Copy Internet-in-a-Box Content Packs to (and from) USB sticks and portable disks.  If teachers' own ZIM files on a USB stick can be hot-plugged into Internet-in-a-Box, that might be supported in future too.  [#828](https://github.com/iiab/iiab/issues/828), [#857](https://github.com/iiab/iiab/issues/857)
* [Lokole](https://ascoderu.ca/) 0.1.26 email for rural communities, students and teachers.  [PR #1284](https://github.com/iiab/iiab/pull/1284), [PR #1305](https://github.com/iiab/iiab/pull/1305)
* Experimental Captive Portal for new users who have trouble typing in http://box, http://box.lan and http://172.18.96.1 &mdash; to help get everyone started right away &mdash; even if they are not familiar with Latin-based keyboards.  Includes [dnsmasq](https://github.com/iiab/iiab/blob/master/vars/local_vars_medium.yml#L51-L60) by default, to improve DNS and DHCP, instead of named/BIND and dhcpd.  Please help us test this on different smartphones!  Implementer docs will emerge off of:  [#608](https://github.com/iiab/iiab/issues/608), [PR #1182](https://github.com/iiab/iiab/pull/1182), [PR #1327](https://github.com/iiab/iiab/pull/1327)
* PREVIEW: OpenStreetMap improvements for implementers customizing regional Map Packs  [#1170](https://github.com/iiab/iiab/issues/1170)
* PREVIEW: Node-RED & Mosquitto (MQTT) support for IoT (Internet of Things) electronics projects.  Coming soon in IIAB 7.0?  [PR #854](https://github.com/iiab/iiab/pull/854)
* FUTURE: Rapid networking & configuration changes that can't wait ~20min for Ansible.  Coming soon in IIAB 7.0?  [#796](https://github.com/iiab/iiab/issues/796)
* FUTURE: Your Raspberry Pi's onboard Wi-Fi hotspot can be used to simultaneously get updates from the Internet.  Coming soon in IIAB 7.0?  [PR #697](https://github.com/iiab/iiab/pull/697), [PR #748](https://github.com/iiab/iiab/pull/748)

### What's Upgraded? (TENTATIVE)

* Internet-in-a-Box's [1-line installer](http://download.iiab.io/6.7/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 is ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin: whether you want ~6, ~12 or ~20 apps!  Implementers please read http://FAQ.IIAB.IO to get to know [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) — as well as the "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" command within IIAB's main directory (/opt/iiab/iiab).
  * This 1-line installer allows setting of passwords for pi and iiab-admin, rapid selection of MIN-sized, MEDIUM-sized or BIG-sized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml), and automatic installation of apt-based OS updates.  Future: auto-reboot(s) could be made even more intelligent, better integration/automation of the torrenting+installing of KA Lite compressed videos (etc) across 7 languages.  Coming soon in IIAB 6.7 or 7.0:  [#872](https://github.com/iiab/iiab/issues/872), [#884](https://github.com/iiab/iiab/issues/884), [#1028](https://github.com/iiab/iiab/issues/1028), [#1189](https://github.com/iiab/iiab/issues/1189)
  * Experimental support for [Debian 10 "Buster"](https://www.debian.org/devel/debian-installer/) is included, in advance of Debian 10's release in 2019.  Support for [Debian "Sid"](http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/amd64/iso-cd/) (AKA Debian's "unstable" bleeding-edge branch) is also improving.
  * [Ansible 2.7](https://docs.ansible.com/ansible/devel/porting_guides/porting_guide_2.7.html) for Internet-in-a-Box configuration management, explaining its steps during IIAB installation.  [#1271](https://github.com/iiab/iiab/pull/1271)
* Kolibri is upgraded to [0.11.0](https://medium.com/kolibri-releases/kolibri-v0-11-is-here-1ba5c878c6ba) ([documentation](https://kolibri.readthedocs.io/en/latest/manage.html)) [#1110](https://github.com/iiab/iiab/issues/1110)
* Calibre is upgraded to [3.37](https://calibre-ebook.com/whats-new)  [#1359](https://github.com/iiab/iiab/issues/1359)
* Calibre-Web (http://box/books) is reinforced  [#1213](https://github.com/iiab/iiab/pull/1213)
* WordPress is upgraded to [5.0.3](https://wordpress.org/news/2019/01/wordpress-5-0-3-maintenance-release/) expected ["2019-01-09"](https://github.com/iiab/iiab/issues/1360), building on the major changes introduced by [5.0](https://wordpress.org/news/2018/12/bebo/) ([technical details](https://make.wordpress.org/core/tag/5-0/))
* Kiwix is upgraded to [0.8.0-2](https://github.com/kiwix/kiwix-tools/blob/master/Changelog)  [#1297](https://github.com/iiab/iiab/pull/1297)
* Nextcloud is upgraded to [Nextcloud 15](https://nextcloud.com/changelog/#latest15) ([blog](https://nextcloud.com/blog/))  [#1048](https://github.com/iiab/iiab/issues/1048)
* Moodle is upgraded to [3.5.4 LTS](https://docs.moodle.org/dev/Moodle_3.5.4_release_notes) expected ["2019-01-14"](https://github.com/iiab/iiab/issues/1296) (building on [3.5 LTS](https://docs.moodle.org/dev/Releases#Moodle_3.5_.28LTS.29))  [#1296](https://github.com/iiab/iiab/issues/1296)
* MediaWiki is upgraded to [1.32.0](https://lists.wikimedia.org/pipermail/mediawiki-announce/2019-January/thread.html) expected ["Jan 7th-11th, 2019"](https://github.com/iiab/iiab/issues/1358)
* Elgg is upgraded to [2.3.10](https://github.com/Elgg/Elgg/blob/2.3.10/CHANGELOG.md)
* Extensive Fixes.  See our [changelog](https://github.com/iiab/iiab/milestone/4?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9/10:

     curl d.iiab.io/install.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-11-13 or higher) installed onto a microSD card large enough for all your content.  Installation usually completes within two hours, if your Internet speed is very fast.  An actual Ethernet cable greatly helps avoid Wi-Fi glitches!  See [download.iiab.io](http://download.iiab.io/) for speed and security tips to hit the ground running.

Finally if you're adventurous, try installing onto [another Linux](https://github.com/iiab/iiab/wiki/IIAB-Platforms), using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by [CONTRIBUTOR NAMES GO HERE] &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's quality content collaborations across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* ?