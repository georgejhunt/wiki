### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.7 will build on [IIAB 6.6](https://github.com/iiab/iiab/wiki/IIAB-6.6-Release-Notes), to be released around October/November ([Wiki](http://wiki.iiab.io/6.7), [GitHub](https://github.com/iiab/iiab/milestone/4)) in service of DIY digital libraries everywhere.

Consider installing a pre-release today, from <a href=http://download.iiab.io/6.7>download.iiab.io/6.7</a> !

### What's New? (TENTATIVE)

* PREVIEW: Copy Internet-in-a-Box Content Packs to (and from) USB sticks and portable disks.  If a teacher's own ZIM files on a USB stick can be hot-plugged into Internet-in-a-Box, that will be considered too.  Coming soon in IIAB 6.7 or 7.0:  [#828](https://github.com/iiab/iiab/issues/828), [#857](https://github.com/iiab/iiab/issues/857)
* PREVIEW: Experimental Captive Portal for new users who have trouble typing in http://box, http://box.lan and http://172.18.96.1 &mdash; to help get everyone started right away &mdash; even if they are not familiar with Latin-based keyboards.  Optionally includes [dnsmasq](https://github.com/iiab/iiab/blob/master/vars/local_vars_medium.yml#L50-L58), to improve DNS etc, instead of named/BIND.  Coming soon in IIAB 6.7 or 7.0.  Implementer docs will emerge off of:  [#608](https://github.com/iiab/iiab/issues/608), [#826](https://github.com/iiab/iiab/issues/826), [PR #870](https://github.com/iiab/iiab/pull/870#issuecomment-406869713)
* PREVIEW: Offline email for students and teachers, using [Lokole](https://ascoderu.ca/).  Coming soon in IIAB 6.7 or 7.0:  [PR #894](https://github.com/iiab/iiab/pull/894)
* PREVIEW: Node-RED & Mosquitto (MQTT) support for IoT (Internet of Things) electronics projects.  Coming soon in IIAB 6.7 or 7.0:  [PR #854](https://github.com/iiab/iiab/pull/854)

### What's Upgraded? (TENTATIVE)

* Internet-in-a-Box's [1-line installer](http://download.iiab.io/6.6/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 is ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin: whether you want ~6, ~12 or ~20 apps!  Implementers please read http://FAQ.IIAB.IO to get to know [/etc/iiab/local_vars.yml](http://wiki.iiab.io/local_vars.yml) — as well as the "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" command within IIAB's main directory (/opt/iiab/iiab).
  * FUTURE: [Ansible 2.7](https://docs.ansible.com/ansible/devel/roadmap/ROADMAP_2_7.html) ([changelog](https://github.com/ansible/ansible/blob/stable-2.7/changelogs/CHANGELOG-v2.7.rst)) helps future-proof Internet-in-a-Box configuration management (ETA 2018-10-04)
  * FUTURE: 1-line installer for IIAB should pre-populate [local_vars.yml](wiki.iiab.io/local_vars.yml), auto-reboot intelligently, and automate the torrenting+installing of KA Lite compressed videos (etc) in 7 languages.  Coming soon in IIAB 6.7 or 7.0:  [#872](https://github.com/iiab/iiab/issues/872), [#884](https://github.com/iiab/iiab/issues/884)
  * FUTURE: Rapid networking & configuration changes that can't wait ~20min for Ansible.  Coming soon in IIAB 6.7 or 7.0:  [#796](https://github.com/iiab/iiab/issues/796)
  * FUTURE: Your Raspberry Pi's onboard Wi-Fi hotspot can be used to simultaneously get updates from the Internet.  Coming soon in IIAB 6.7 or 7.0:  [PR #697](https://github.com/iiab/iiab/pull/697), [PR #748](https://github.com/iiab/iiab/pull/748)
* WordPress is upgraded to [WordPress 5.0+](https://wordpress.org/news/) (ETA October 2018)
* Nextcloud is upgraded to [Nextcloud 14](https://nextcloud.com/blog/) (ETA 2018-09-06)
* Moodle is upgraded to [3.5.2+ LTS](https://docs.moodle.org/dev/Releases) (ETA 2018-09-10)
* Extensive Fixes.  See our [changelog](https://github.com/iiab/iiab/milestone/4?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9:

     curl download.iiab.io/6.7/install.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-06-27 or higher) installed onto a microSD card large enough for all your content.  Installation usually completes within two hours, if your Internet speed is very fast.  An actual Ethernet cable greatly helps avoid Wi-Fi glitches!  See [download.iiab.io/6.7](http://download.iiab.io/6.7/) for speed and security tips to hit the ground running.

Finally if you're adventurous, try installing onto [another Linux](https://github.com/iiab/iiab/wiki/IIAB-Platforms), using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by [CONTRIBUTOR NAMES GO HERE] &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's quality content collaborations across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* ?