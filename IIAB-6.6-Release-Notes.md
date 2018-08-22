### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.6 incorporates an extensive amount of teacher feedback from [IIAB 6.5](https://github.com/iiab/iiab/wiki/IIAB-6.5-Release-Notes), and will be released in August ([Wiki](http://wiki.iiab.io/6.6), [GitHub](https://github.com/iiab/iiab/milestone/3)) in service of DIY digital libraries everywhere.

FOCUS: Testers’ + Teachers’ + (field) Techs’ immediate needs (<a href=https://github.com/iiab/iiab/pull/840>checklist</a>).

CLARIF: Larger architectural improvements will be deferred to [IIAB 6.7](http://wiki.iiab.io/6.7) or [IIAB 7.0](https://github.com/iiab/iiab/milestone/5).

_TODAY: Consider installing a <a href=http://download.iiab.io/6.6>pre-release of IIAB 6.6</a> !_

### What's New? (TENTATIVE)

* Experimental support for [Kolibri 0.10.x](https://blog.learningequality.org/kolibri-v0-10-is-released-4e673398f116) ([background](https://blog.learningequality.org/startwithkolibri-58227e98dde)) which is similar to [KA Lite](https://learningequality.org/ka-lite/) but offers many more curriculum design tools beyond Khan Academy, to create, remix and refine offline content packs:  [#841](https://github.com/iiab/iiab/issues/841#issuecomment-405767755)
* [Sugarizer 1.0.1](http://sugarizer.org) is a "kids construct" learning environment originally from One Laptop Per Child, with easy accounts for kids to save their work.  Please use http://box:8089 after installing Internet-in-a-Box, as short/clean/mnemonic URL's like http://box/sugarizer are currently broken (hopefully to be fixed soon; Sugarizer 1.x is a major change from earlier versions so please bear with us and [provide feedback](http://FAQ.IIAB.IO#What_are_the_best_places_for_community_support.3F)!)  [#798](https://github.com/iiab/iiab/issues/798#issuecomment-405609004), [PR #888](https://github.com/iiab/iiab/pull/888#issuecomment-404370082)
* OpenStreetMap Content Packs are now extremely fast to download, thanks to compact vector-based tiles (instead of the older bitmap tiles).  Online samples are viewable for ["Planet Earth"](http://medbox.iiab.me/modules/en-osm-omt-min/) (just the basics) or choose superset ["Central America"](http://medbox.iiab.me/modules/en-osm-omt-central-am/) (including [Haiti and a lot of South America](https://openmaptiles.com/downloads/central-america/)).  Further regions can be downloaded from [openmaptiles.org](https://openmaptiles.com/downloads/planet/) &mdash; please see the [README](https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/README.md) and [Design Decisions](https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/Design-Decisions.md) before downloading from [download.iiab.io/content/OSM/vector-tiles](http://download.iiab.io/content/OSM/vector-tiles/).  Dev Notes:  [#877](https://github.com/iiab/iiab/issues/877#issuecomment-405935272)
* PREVIEW: Easy backup, duplication and shrinking of Internet-in-a-Box (IIAB) microSD cards using [IMAGER](http://download.iiab.io/packages/imager/).  Allows teachers in the field to copy from any microSD to any other microSD that's big enough.  These are teachers who cannot realistically use Linux command-line tools to [truncate (AKA shrink, or minify)](https://github.com/iiab/iiab-factory/tree/master/box/rpi) and then [dd](https://www.linuxnix.com/what-you-should-know-about-linux-dd-command/).  Please see pre-release [screen shots](https://github.com/iiab/iiab-factory/blob/master/box/rpi/imager/docs/README.md).  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#827](https://github.com/iiab/iiab/issues/827)
* PREVIEW: Copy Internet-in-a-Box Content Packs to (and from) USB sticks and portable disks.  If a teacher's own ZIM files on a USB stick can be hot-plugged into Internet-in-a-Box, that will be considered too.  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#828](https://github.com/iiab/iiab/issues/828), [#857](https://github.com/iiab/iiab/issues/857)
* PREVIEW: Experimental Captive Portal for new users who have trouble typing in http://box, http://box.lan and http://172.18.96.1 &mdash; to help get everyone started right away &mdash; even if they are not familiar with Latin-based keyboards.  Optionally includes [dnsmasq](https://github.com/iiab/iiab/blob/master/vars/local_vars_medium.yml#L50-L58), to improve DNS etc, instead of named/BIND.  Implementer docs will emerge off of:  [#608](https://github.com/iiab/iiab/issues/608), [#826](https://github.com/iiab/iiab/issues/826), [PR #870](https://github.com/iiab/iiab/pull/870#issuecomment-406869713)
* PREVIEW: Offline email for students and teachers, using [Lokole](https://ascoderu.ca/).  Not yet landed but coming soon in IIAB 6.7 or 7.0:  [PR #894](https://github.com/iiab/iiab/pull/894)
* PREVIEW: Node-RED & Mosquitto (MQTT) support for IoT (Internet of Things) electronics projects.  Not yet landed but coming soon in IIAB 6.7 or 7.0:  [PR #854](https://github.com/iiab/iiab/pull/854)

### What's Upgraded? (TENTATIVE)

* Internet-in-a-Box's [1-line installer](http://download.iiab.io/6.6/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 is ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin: whether you want ~6, ~12 or ~20 apps!  Implementers please read http://FAQ.IIAB.IO to get to know [/etc/iiab/local_vars.yml](http://wiki.iiab.io/local_vars.yml) — as well as the commands "[./iiab-install](https://github.com/iiab/iiab/blob/master/iiab-install)" and "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" within IIAB's main directory (/opt/iiab/iiab).
  * Regional communities can now instantly re-use their favorite/custom IIAB configurations (much like IIAB microSD card cloning, also coming soon!)  *Simply drop this file in place* (/etc/iiab/local_vars.yml) and then start your IIAB install on any fresh/new machine -- next time you run `curl download.iiab.io/6.6/install.txt | sudo bash`
  * You can now RE-run "curl download.iiab.io/6.6/install.txt | sudo bash" (after Internet glitches, or on a brand-new machine if you copied someone else's /etc/iiab/local_vars.yml) thanks to IIAB's new unified installer.
  * *Explanations in context as IIAB is installing, and major improvements in Ansible code readability.*
  * All documentation overhauled to reflect the new, more convenient location for your IIAB definition/core settings: [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml)
  * OpenVPN remote support is beefed up, enabled by variable openvpn_handle in [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml), that is then stored in /etc/iiab/openvpn_handle:  [#995](https://github.com/iiab/iiab/issues/995), [PR #1000](https://github.com/iiab/iiab/pull/1000)
  * Experimental support for [Debian 10 "Buster"](https://www.debian.org/devel/debian-installer/) is included, in advance of Debian 10's release in 2019.  Debian Sid (AKA the "unstable" bleeding edge branch of Debian 10) might also work.
  * FUTURE: 1-line installer for IIAB should pre-populate [local_vars.yml](wiki.iiab.io/local_vars.yml), auto-reboot intelligently, and automate the torrenting+installing of KA Lite compressed videos (etc) in 7 languages.  Coming soon in IIAB 6.7 or 7.0:  [#872](https://github.com/iiab/iiab/issues/872), [#884](https://github.com/iiab/iiab/issues/884)
  * FUTURE: Rapid networking & configuration changes that can't wait ~20min for Ansible.  Coming soon in IIAB 6.7 or 7.0:  [#796](https://github.com/iiab/iiab/issues/796)
  * FUTURE: Your Raspberry Pi's onboard Wi-Fi hotspot can be used to simultaneously get updates from the Internet.  Not yet landed but coming soon in IIAB 6.7 or 7.0:  [PR #697](https://github.com/iiab/iiab/pull/697), [PR #748](https://github.com/iiab/iiab/pull/748)
* Calibre E-Book server [3.29+](https://calibre-ebook.com/whats-new) installation procedure is more ruggedized.  Allows teachers to add and delete books using the web interface, edit book metadata, and convert books to other formats like PDF and EPUB.  IIAB's installer now creates the Calibre's default usernames and passwords listed in http://FAQ.IIAB.IO so teachers can begin refining their collection immediately.
  * PREVIEW: An elegant and friendlier [calibre-web](https://github.com/janeczku/calibre-web) web interface has not yet landed but is coming soon in IIAB 6.6 or 6.7:  [#816](https://github.com/iiab/iiab/issues/816), [PR #999](https://github.com/iiab/iiab/pull/999)
* Media-rich and searchable offline (ZIM) content thanks to an even far better [Kiwix](http://www.kiwix.org/) engine 0.6.0 (2018-06-20) under the hood, _watch out Google here we come :-)_
* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.5](https://github.com/learningequality/ka-lite/releases/tag/v0.17.5) with installation greatly streamlined.
* Wikipedia's own MediaWiki [1.31.0 LTS](https://www.mediawiki.org/wiki/MediaWiki_1.31) is now part of [BIG-sized](http://wiki.iiab.io/local_vars_big.yml) installs of IIAB, for doc collaboration.  You can also install and enable it from [local_vars.yml](http://wiki.iiab.io/local_vars.yml) (typically on Lines 143 and 144).
* Nextcloud is upgraded to [13.0.5](https://nextcloud.com/blog/nextcloud-13.0.5-and-12.0.10-secure-and-stabilize-your-server/) ([changelog](https://nextcloud.com/changelog/)) based on [Nextcloud 13](https://nextcloud.com/blog/nextcloud-13-brings-secure-file-sync-and-collaboration-to-the-next-level/).
* WordPress is upgraded to [4.9.8](https://wordpress.org/news/2018/08/wordpress-4-9-8-maintenance-release/) including “Try Gutenberg” visual/block editor preview.  Reinforces [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) privacy compliance, based on WordPress [4.9](https://wordpress.org/news/2017/11/tipton/).
* Moodle is upgraded to [3.5.1+ LTS](https://docs.moodle.org/dev/Moodle_3.5.1_release_notes) based on [3.5 LTS](https://docs.moodle.org/dev/Moodle_3.5_release_notes) for privacy, better quizzes, speed, messaging integration and modern usability ([preview](https://www.moodlenews.com/2018/privacy-better-quizzes-faster-and-modern-the-latest-scoop-on-moodle-3-5/), [new features](https://docs.moodle.org/35/en/New_features)).
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.8](https://github.com/Elgg/Elgg/blob/2.3.8/CHANGELOG.md).
* phpMyAdmin is upgraded to [4.8.3](https://www.phpmyadmin.net/news/).
* More comprehensive Offline Docs, onboard your Internet-in-a-Box and available to all in the field, at [http://box/info](http://box/info) &mdash; including instructions on [how to upgrade (or reinstall while offline) your IIAB server apps](http://FAQ.IIAB.IO#Can_I_upgrade_or_reinstall_server_apps.3F) a.k.a. IIAB services.
* IIAB's [Ansible playbooks](https://github.com/iiab/iiab/tree/master/roles) are far more readable, with modern indentation, instead of cramming too many things into 1 line.
* Extensive Fixes.  See our [changelog](https://github.com/iiab/iiab/milestone/3?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9:

     curl download.iiab.io/6.6/install.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-06-27 or higher) installed onto a microSD card large enough for content.  Installation usually completes within two hours, if your Internet speed is very fast.  An actual Ethernet cable helps avoid Wi-Fi glitches!  See [download.iiab.io/6.6](http://download.iiab.io/6.6/) for speed and security tips to hit the ground running.

Finally if you are adventurous, try installing onto CentOS, using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by [CONTRIBUTOR NAMES GO HERE] &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's [quality content collaborations](http://boxing.team) across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* Short/memorizable URL's like http://box/kolibri and http://box/sugarizer are currently broken.  Use [http://box:8009](http://box:8009) and [http://box:8089](http://box:8089) in the interim:  [#923](https://github.com/iiab/iiab/issues/923)
* Raspberry Pi's internal Wi-Fi hotspot very occasionally fails to provide IP addresses, when Ethernet ISN'T plugged in? 
 [#989](https://github.com/iiab/iiab/issues/989)
* Raspberry Pi's internal Wi-Fi hotspot very occasionally fails within an hour of booting, when Ethernet IS plugged in?  [#926](https://github.com/iiab/iiab/issues/926)
* Calibre 3.27.1 (like 3.24.x and 3.25) had prevented IIAB microSD's from booting in Raspberry Pi Zero W.  If this recurs in a future version of Calibre, those who rely on RPi Zero W would need to turn off Calibre's installation in /etc/iiab/local_vars.yml during installation of IIAB:  [#952](https://github.com/iiab/iiab/issues/952)
* USB memory sticks may need to be [removed and re-inserted](https://github.com/iiab/iiab/issues/329#issuecomment-333330362) into your Internet-in-a-Box before [Teacher Content](http://FAQ.IIAB.IO#Can_teachers_display_their_own_content.3F) appears at http://box/usb e.g. if stick was inserted just prior to a cold boot:  [#329](https://github.com/iiab/iiab/issues/329)
* Nextcloud ([http://box/nextcloud](http://box/nextcloud)) logins/logouts are much faster but remain slow:  [#401](https://github.com/iiab/iiab/issues/401)
* Set a default locale in your OS in /etc/default/locale (also the "locale" command and $LANG environment variable should show the same, e.g. "C.UTF-8" or "en_US.UTF-8") to avoid language restrictions upon re-installing WordPress.