### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.7 will build on [IIAB 6.6](https://github.com/iiab/iiab/wiki/IIAB-6.6-Release-Notes), to be released in January 2019 ([Wiki](http://wiki.laptop.org/go/IIAB/6.7), [GitHub](https://github.com/iiab/iiab/milestone/4)) in service of DIY digital libraries everywhere.

Consider installing a pre-release today, from <a href=http://download.iiab.io/6.7/>download.iiab.io/6.7</a> !

### What's New? (TENTATIVE)

* Copy Internet-in-a-Box Content Packs to (and from) USB sticks and portable disks.  If teachers' own ZIM files on a USB stick can be hot-plugged into Internet-in-a-Box, that might be supported in future too.  <sub><sub>[#828](https://github.com/iiab/iiab/issues/828)</sub></sub>
* [Lokole 0.1.26](https://ascoderu.ca/) email for rural communities, students and teachers.  <sub><sub>[PR #1305](https://github.com/iiab/iiab/pull/1305)</sub></sub>
* Experimental Captive Portal for new users who have trouble typing in http://box, http://box.lan and http://172.18.96.1 &mdash; to help get everyone started right away &mdash; even if they are not familiar with Latin-based keyboards.  Includes [dnsmasq](https://github.com/iiab/iiab/blob/master/vars/local_vars_medium.yml#L51-L60) by default, to improve DNS and DHCP, instead of named/BIND and dhcpd.  Please help us test this on different smartphones!  Implementer docs emerging off:  <sub><sub>[#1182](https://github.com/iiab/iiab/issues/1182)</sub></sub>
* FUTURE: Node-RED & Mosquitto (MQTT) support for IoT (Internet of Things) electronics projects.  Coming soon in IIAB 7.0?  <sub><sub>[PR #854](https://github.com/iiab/iiab/pull/854)</sub></sub>
* FUTURE: OpenStreetMap improvements for implementers customizing regional Map Packs.  Coming soon in IIAB 7.0?  <sub><sub>[#1170](https://github.com/iiab/iiab/issues/1170)</sub></sub>
* FUTURE: Rapid networking & configuration changes that can't wait ~20min for Ansible.  Coming soon in IIAB 7.0?  <sub><sub>[#796](https://github.com/iiab/iiab/issues/796)</sub></sub>
* FUTURE: Your Raspberry Pi's onboard Wi-Fi hotspot can be used to simultaneously get updates from the Internet.  Coming soon in IIAB 7.0?  <sub><sub>[PR #697](https://github.com/iiab/iiab/pull/697), [PR #748](https://github.com/iiab/iiab/pull/748)</sub></sub>

### What's Upgraded? (TENTATIVE)

* Internet-in-a-Box's [1-line installer](http://download.iiab.io/6.7/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 is ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin: whether you want ~6, ~12 or ~20 apps!  Implementers please read http://FAQ.IIAB.IO to get to know [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) — as well as the "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" command within IIAB's main directory (/opt/iiab/iiab).
  * This 1-line installer allows setting of passwords for pi and iiab-admin, rapid selection of MIN-sized, MEDIUM-sized or BIG-sized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml), and automatic installation of apt-based OS updates.  Future: auto-reboot(s) could be made even more intelligent, with better integration/automation of the torrenting+installing of KA Lite compressed videos (etc) across 7 languages.  <sub><sub>[#1028](https://github.com/iiab/iiab/issues/1028)</sub></sub>
  * Experimental support for [Debian 10 "Buster"](https://www.debian.org/devel/debian-installer/) is included, in advance of Debian 10's release in 2019.  Support for [Debian "Sid"](http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/amd64/iso-cd/) (AKA Debian's "unstable" bleeding-edge branch) is also improving.
  * [Ansible 2.7](https://docs.ansible.com/ansible/devel/porting_guides/porting_guide_2.7.html) for Internet-in-a-Box configuration management, explaining its steps during IIAB installation.  <sub><sub>[#1271](https://github.com/iiab/iiab/pull/1271)</sub></sub>
* [Kolibri 0.11.0](https://medium.com/kolibri-releases/kolibri-v0-11-is-here-1ba5c878c6ba) ([docs](https://kolibri.readthedocs.io/en/latest/manage.html)) with URL _box:8009_  <sub><sub>[#1110](https://github.com/iiab/iiab/issues/1110)</sub></sub>
* [Calibre 3.37](https://calibre-ebook.com/whats-new) with URL _box:8080_  <sub><sub>[#1359](https://github.com/iiab/iiab/issues/1359)</sub></sub>
* [Calibre-Web](https://github.com/janeczku/calibre-web#about) with URL _box/books_  <sub><sub>[#1213](https://github.com/iiab/iiab/pull/1213)</sub></sub>
* [WordPress 5.0.3](https://wordpress.org/news/2019/01/wordpress-5-0-3-maintenance-release/) building on the major changes introduced by [5.0](https://wordpress.org/news/2018/12/bebo/) with URL _box/wordpress_  <sub><sub>[#1360](https://github.com/iiab/iiab/issues/1360)</sub></sub>
* [Kiwix 0.8.0-2](https://github.com/kiwix/kiwix-tools/blob/master/Changelog) with URL _box/kiwix_  <sub><sub>[PR #1297](https://github.com/iiab/iiab/pull/1297)</sub></sub>
* [Nextcloud 15.0.1](https://nextcloud.com/changelog/#latest15) ([blog](https://nextcloud.com/blog/)) expected "2019-01-10" with URL _box/nextcloud_  <sub><sub>[#1361](https://github.com/iiab/iiab/issues/1361)</sub></sub>
* [Moodle 3.5.4 LTS](https://docs.moodle.org/dev/Moodle_3.5.4_release_notes) expected "2019-01-14" (building on [3.5 LTS](https://docs.moodle.org/dev/Releases#Moodle_3.5_.28LTS.29)) with URL _box/moodle_  <sub><sub>[#1296](https://github.com/iiab/iiab/issues/1296)</sub></sub>
* [MediaWiki 1.32.0](https://lists.wikimedia.org/pipermail/mediawiki-announce/2019-January/thread.html) expected "Jan 7th-11th, 2019" with URL _box/mediawiki_  <sub><sub>[#1358](https://github.com/iiab/iiab/issues/1358)</sub></sub>
* [Elgg 2.3.10](https://github.com/Elgg/Elgg/blob/2.3.10/CHANGELOG.md) with URL _box/elgg_  <sub><sub>[PR #1342](https://github.com/iiab/iiab/pull/1342)</sub></sub>
* [phpMyAdmin 4.8.4](https://www.phpmyadmin.net/)  <sub><sub>[#1365](https://github.com/iiab/iiab/pull/1365)</sub></sub>
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