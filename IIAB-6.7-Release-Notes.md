### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.7 will build on [IIAB 6.6](https://github.com/iiab/iiab/wiki/IIAB-6.6-Release-Notes), to be released in February 2019 ([Wiki](http://wiki.laptop.org/go/IIAB/6.7), [GitHub](https://github.com/iiab/iiab/milestone/4)) in service of DIY digital libraries everywhere.

_Consider installing a pre-release today, from <a href=http://download.iiab.io/6.7/>download.iiab.io/6.7</a> !_

### What's New?

* Drag & Drop your favorite Content Packs into position to create the best visual menu for your school or medical clinic's Internet-in-a-Box.  [Screencast videos](http://d.iiab.io/content/videos/) are emerging alongside written [documentation](https://github.com/iiab/iiab/wiki/IIAB-Menuing#2019-additions) to help you DIY your own Internet-in-a-Box digital library.  A [WordPress plugin](https://github.com/kananigit/iiab-menu-plugin) is also emerging, so you can integrate IIAB Apps and Content Packs into a larger WordPress site.  <sub><sub>[#1393](https://github.com/iiab/iiab/issues/1393)</sub></sub>
* Copy Internet-in-a-Box Content Packs to (and from) USB sticks and portable disks.  If teachers' own ZIM files on a USB stick can be hot-plugged into Internet-in-a-Box, that might be supported in future too.  <sub><sub>[#828](https://github.com/iiab/iiab/issues/828)</sub></sub>
* Experimental Captive Portal for new users who have trouble typing in http://box, http://box.lan and http://172.18.96.1 &mdash; to help everyone get started right away &mdash; even if they're not familiar with Latin-based keyboards.  Includes [dnsmasq](http://www.thekelleys.org.uk/dnsmasq/doc.html) by default, to improve DNS and DHCP, instead of named/BIND and dhcpd.  Please read [Known Issues](#known-issues) and [help us test this](http://wiki.laptop.org/go/IIAB/FAQ#Captive_Portal_Administration:_What_tips_.26_tricks_exist.3F) on different smartphones!  <sub><sub>[#1182](https://github.com/iiab/iiab/issues/1182)</sub></sub>
* [Asterisk 16 & FreePBX 15](https://github.com/iiab/iiab/tree/master/roles/pbx#pbx-readme) for Voice over IP and rural telephony.  Works on Ubuntu 18.04, Debian 9 "Stretch" and experimentally supports Raspberry Pi too!  <sub><sub>[PR #1405](https://github.com/iiab/iiab/pull/1405)</sub></sub>
* [Lokole 0.1.38](https://github.com/iiab/iiab/tree/master/roles/lokole#lokole-readme) email for rural communities, students and teachers, with URL _box/lokole_  <sub><sub>[PR #1305](https://github.com/iiab/iiab/pull/1305)</sub></sub>
* [Minetest](https://github.com/iiab/iiab/tree/master/roles/minetest#minetest-readme) is a [Minecraft](https://en.wikipedia.org/wiki/Minecraft)-inspired creative/explorational building blocks game, including multiplayer server and additional mods.  <sub><sub>[PR #1471](https://github.com/iiab/iiab/pull/1471)</sub></sub>
* [Mosquitto 1.4+ (MQTT)](https://github.com/iiab/iiab/tree/master/roles/mosquitto#mosquitto-readme) & [Node-RED 0.19.5](https://github.com/iiab/iiab/tree/master/roles/nodered#nodered-readme) support for IoT (Internet of Things) electronics projects, with URL _box/nodered_  <sub><sub>[PR #1398](https://github.com/iiab/iiab/pull/1398)</sub></sub>
* _A brand-new [visual comparison table](http://wiki.laptop.org/go/IIAB/FAQ#What_services_.28IIAB_apps.29_are_suggested_during_installation.3F) helping guide your choice of what services (IIAB Apps) to install._

### What's Upgraded?

* Internet-in-a-Box's (IIAB) [1-line installer](http://download.iiab.io/6.7/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 is ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  [**Pick your favorite suite**](http://wiki.laptop.org/go/IIAB/FAQ#What_services_.28IIAB_apps.29_are_suggested_during_installation.3F) of IIAB apps the very moment you begin: whether you want ~6, ~12 or ~20 apps (MIN-sized, MEDIUM-sized, or BIG-sized).  Implementers please read http://FAQ.IIAB.IO to get to know [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F) — as well as the "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" command within IIAB's main directory (/opt/iiab/iiab).
  * IIAB's 1-line installer encourages you to secure the passwords for 'pi' and 'iiab-admin', offers you a rapid/ selection among MIN-sized, MEDIUM-sized or BIG-sized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml), then automatically installs apt-based OS updates.  Future: auto-reboot(s) could be made even more intelligent, with better integration/automation of the torrenting+installing of KA Lite compressed videos (etc) across 7 languages.  <sub><sub>[#1028](https://github.com/iiab/iiab/issues/1028)</sub></sub>
  * Experimental support for [Debian 10 "Buster"](https://www.debian.org/devel/debian-installer/) is included, in advance of Debian 10's release in mid-2019 ([install tips](https://github.com/iiab/iiab/issues/1387)).  <sub><sub>[#1387](https://github.com/iiab/iiab/issues/1387)</sub></sub>  Support for [Debian "Sid"](https://wiki.debian.org/DebianUnstable) (AKA Debian's "unstable" bleeding-edge branch) and for [Ubermix](https://github.com/iiab/iiab/wiki/IIAB-Platforms#operating-systems) (allowing teachers to wipe PC/workstations clean) are also improving.
  * [Ansible 2.7](https://docs.ansible.com/ansible/devel/porting_guides/porting_guide_2.7.html) for IIAB configuration management, better explaining IIAB installation steps.  <sub><sub>[#1271](https://github.com/iiab/iiab/pull/1271)</sub></sub>
* [Kolibri 0.11.1](https://github.com/iiab/iiab/tree/master/roles/kolibri) ([release notes](https://medium.com/kolibri-releases/kolibri-v0-11-is-here-1ba5c878c6ba), [docs](https://kolibri.readthedocs.io/en/latest/manage.html)) with URL _box/kolibri_  <sub><sub>[#1110](https://github.com/iiab/iiab/issues/1110)</sub></sub>
* [Kiwix 0.9.0](https://github.com/kiwix/kiwix-tools/blob/master/Changelog) with URL _box/kiwix_  <sub><sub>[PR #1433](https://github.com/iiab/iiab/pull/1433)</sub></sub>
* [Calibre 3.39.1](https://calibre-ebook.com/whats-new) with URL _box:8080_  <sub><sub>[#1413](https://github.com/iiab/iiab/issues/1413)</sub></sub>
* [Calibre-Web](https://github.com/janeczku/calibre-web#about) ([docs](https://github.com/iiab/iiab/tree/master/roles/calibre-web)) with URL _box/books_  <sub><sub>[#1213](https://github.com/iiab/iiab/pull/1213)</sub></sub>
* [Sugarizer 1.1.0](https://sugarizer.org) with URL _box/sugarizer_  <sub><sub>[PR #1430](https://github.com/iiab/iiab/pull/1430)</sub></sub>
* [WordPress 5.1](https://wordpress.org/news/) builds on the new block editor introduced by [5.0](https://wordpress.org/news/2018/12/bebo/), with URL _box/wordpress_  <sub><sub>[#1360](https://github.com/iiab/iiab/issues/1360)</sub></sub>
* [Nextcloud 15.0.4](https://nextcloud.com/changelog/#latest15) ([blog](https://nextcloud.com/blog/)) with URL _box/nextcloud_  <sub><sub>[#1361](https://github.com/iiab/iiab/issues/1361)</sub></sub>
* [Moodle 3.5.4 LTS](https://docs.moodle.org/dev/Moodle_3.5.4_release_notes) building on [3.5 LTS](https://docs.moodle.org/dev/Releases#Moodle_3.5_.28LTS.29), with URL _box/moodle_  <sub><sub>[#1296](https://github.com/iiab/iiab/issues/1296)</sub></sub>
* [MediaWiki 1.32.0](https://www.mediawiki.org/wiki/Release_notes/1.32) with URL _box/mediawiki_  <sub><sub>[#1358](https://github.com/iiab/iiab/issues/1358)</sub></sub>
* [DokuWiki 2018-04-22b](https://www.dokuwiki.org/changes) with URL _box/wiki_  <sub><sub>[PR #1388](https://github.com/iiab/iiab/pull/1388)</sub></sub>
* [Elgg 2.3.10](https://github.com/Elgg/Elgg/blob/2.3.10/CHANGELOG.md) with URL _box/elgg_  <sub><sub>[PR #1342](https://github.com/iiab/iiab/pull/1342)</sub></sub>
* [phpMyAdmin 4.8.5](https://www.phpmyadmin.net/) for remote administration of MySQL  <sub><sub>[#1365](https://github.com/iiab/iiab/pull/1365)</sub></sub>
* [Node.js 10.x LTS](https://technology.condenast.com/story/10-for-10-a-scenic-tour-of-nodejs-10-lts) for Asterisk/FreePBX, Node-RED & Sugarizer  <sub><sub>[PR #1405](https://github.com/iiab/iiab/pull/1405)</sub></sub>
* [MongoDB 3.0.14+](https://www.mongodb.com/mongodb-3.0) on Raspberry Pi for Sugarizer  <sub><sub>[PR #1430](https://github.com/iiab/iiab/pull/1430)</sub></sub>
* Extensive Fixes.  See our [changelog](https://github.com/iiab/iiab/milestone/4?closed=1) of accomplishments!

### What's might future versions bring?

* OpenStreetMap improvements for implementers needing vivid [regional Map Packs](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_add_zoomable_maps_for_my_region.3F).  <sub><sub>[#877](https://github.com/iiab/iiab/issues/877#issuecomment-405935272)</sub></sub>
* Easily editable Content Pack descriptions & logos, for your community's main page (http://box).  <sub><sub>[#1002](https://github.com/iiab/iiab/issues/1002#issuecomment-462183401)</sub></sub>
* Captive Portal improvements, that work on more/different smartphones.  <sub><sub>[#1182](https://github.com/iiab/iiab/issues/1182)</sub></sub>
* Rapid networking & configuration changes that can't wait ~20min for Ansible.  <sub><sub>[#796](https://github.com/iiab/iiab/issues/796)</sub></sub>
* Your Raspberry Pi's (built-in) Wi-Fi knowledge hotspot can be made to broadcast _and_ (simultaneously) get updates from the Internet.  <sub><sub>[PR #697](https://github.com/iiab/iiab/pull/697), [PR #748](https://github.com/iiab/iiab/pull/748)</sub></sub>
* Please help us make this happen by reviewing the [IIAB 7.0 Milestone](https://github.com/iiab/iiab/milestone/5).

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9/10.  IIAB's 1-line installer lets you [quickly choose](http://wiki.laptop.org/go/IIAB/FAQ#What_services_.28IIAB_apps.29_are_suggested_during_installation.3F) how much to install: (MIN-sized, MEDIUM-sized or BIG-sized)

     curl d.iiab.io/install.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-11-13 or higher) installed onto a microSD card large enough for all your content.  Installation usually completes within 1-to-3 hours, if your Internet speed is fast.  An actual Ethernet cable greatly helps avoid Wi-Fi glitches!  See [download.iiab.io](http://download.iiab.io/) for speed and security tips to hit the ground running.

Finally if you're adventurous, try installing onto [another Linux](https://github.com/iiab/iiab/wiki/IIAB-Platforms), using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by T.K. Kang, Eric Nitschke, Joshua Kanani, Josh Dennis, Arky R., Matt Johnson, James Heilman, Sam Zidovetzki, Reno McKenzie, Anish Mangal, Avni Khatri, Blondel Mondésir, George Hunt, Tim Moody, Jerry Vonau, Adam Holt &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's quality content collaborations across ALL communities!_

Join our Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* [Captive Portal](http://wiki.laptop.org/go/IIAB/FAQ#Captive_Portal_Administration:_What_tips_.26_tricks_exist.3F) currently doesn't work if IIAB is installed on OS's other than Raspbian.  Caution: this prototype functionality might not work at all if an Ethernet cable is not simultaneously in use.  <sub><sub>[#1366](https://github.com/iiab/iiab/issues/1366)</sub></sub> <sub><sub>[#1504](https://github.com/iiab/iiab/issues/1504)</sub></sub>
* If installing IIAB on Debian 10 ("Buster") pre-releases, a few [manual steps](https://github.com/iiab/iiab/issues/1387) may be required.  <sub><sub>[#1387](https://github.com/iiab/iiab/issues/1387)</sub></sub>
* dnsmasq does not start reliably on Ubuntu 16.04 &mdash; please use [Ubuntu 18.04](https://github.com/iiab/iiab/wiki/IIAB-Platforms#operating-systems) instead.  <sub><sub>[#1469](https://github.com/iiab/iiab/issues/1469)</sub></sub>
* Kolibri's systemd service sometimes times out (fails to start) during the 1st reboot of IIAB, on Ubuntu 18.04 and possible other OS's too.  As of 2019-02-11, the workaround is to run "systemctl start kolibri" &mdash; or simply to reboot.  <sub><sub>[#1489](https://github.com/iiab/iiab/issues/1489)</sub></sub>
* FreePBX (for Asterisk) fails to (re)start intermittently, on Raspberry Pi especially.  <sub><sub>[#1493](https://github.com/iiab/iiab/issues/1493)</sub></sub>
* Node.js applications like Asterisk/FreePBX, Node-RED and Sugarizer [won't work](https://nodered.org/docs/hardware/raspberrypi#swapping-sd-cards) on Raspberry Pi Zero W (ARM6) *if* you installed Node.js while on RPi 3 or 3 B+ (ARM7).  If necessary, run `apt remove nodejs` then `cd /opt/iiab/iiab` then [./runrole nodejs](https://github.com/iiab/iiab/blob/master/roles/nodejs/tasks/main.yml) _on the Raspberry Pi Zero W itself_ — before proceeding to install Asterisk/FreePBX, Node-RED and/or Sugarizer.