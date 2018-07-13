### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.6 incorporates an extensive amount of teacher feedback from [IIAB 6.5](https://github.com/iiab/iiab/wiki/IIAB-6.5-Release-Notes), and will be released on in July or August ([Wiki](http://wiki.iiab.io/6.6), [GitHub](https://github.com/iiab/iiab/milestone/3)) in service of DIY digital libraries everywhere.

FOCUS: testers’ + teachers’ + (field) techs’ immediate needs (<a href=https://github.com/iiab/iiab/pull/840>checklist</a>).

CLARIF: Larger architectural improvements will be deferred to [IIAB 6.7](http://wiki.iiab.io/6.7) or [IIAB 7.0](https://github.com/iiab/iiab/milestone/5).

_TODAY: Consider installing a <a href=http://download.iiab.io/6.6>pre-release of IIAB 6.6</a> !_

### What's New? (TENTATIVE)

* [Sugarizer 1.0.1](http://sugarizer.org) is a kids-build-their-own learning environment originally from One Laptop Per Child, with easy accounts for kids to save their work.  Please use http://box:8089 for now, as short/memorizable URL's like http://box/sugarizer are currently broken (hopefully to be fixed soon; Sugarizer 1.x is a major change from earlier versions so please bear with us and [provide feedback](http://FAQ.IIAB.IO#What_are_the_best_places_for_community_support.3F)!)
* Vector-based OpenStreetMap Content Packs that are extremely compact and fast to download.  Online samples are viewable for ["Planet Earth"](http://medbox.iiab.me/modules/en-osm-omt-min/) (just the basics) and ["Central America"](http://medbox.iiab.me/modules/en-osm-omt-central-am/).  Further regions can be downloaded from [openmaptiles.org](http://openmaptiles.org) &mdash; please see the [README](https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/README.md) and [Dev Notes](https://github.com/georgejhunt/iiab/wiki/Vector-Tile-Research), before downloading from [download.iiab.io/content/OSM/vector-tiles](http://download.iiab.io/content/OSM/vector-tiles/):  [#877](https://github.com/iiab/iiab/issues/877) [iiab/iiab-factory#32](https://github.com/iiab/iiab-factory/pull/32)
* Experimental Captive Portal for new users who have trouble typing in http://box, http://box.lan and http://172.18.96.1 &mdash; to help get everyone started right away &mdash; even if they are not familiar with Latin-based keyboards.  Optionally includes [dnsmasq](https://github.com/iiab/iiab/blob/master/vars/local_vars_medium.yml#L50-L58), to improve DNS etc, instead of named/BIND.  Implementer docs will emerge off of: [#870](https://github.com/iiab/iiab/pull/870)
* PREVIEW: Node-RED & Mosquitto (MQTT) support for IoT/electronics projects.  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#854](https://github.com/iiab/iiab/pull/854)
* PREVIEW: Experimental support for [Kolibri 0.10.0](https://blog.learningequality.org/kolibri-v0-10-is-released-4e673398f116), which is similar to [KA Lite](https://learningequality.org/ka-lite/) but offers many more curriculum design tools beyond Khan Academy, to create and refine offline content packs.  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#841](https://github.com/iiab/iiab/issues/841)
* PREVIEW: Easy backup & duplication of Internet-in-a-Box (IIAB) microSD's.  Allows teachers in the field to copy from any microSD to any other microSD with sufficient space.  These are teachers who cannot realistically use Linux command-line tools to [truncate (AKA minify)](https://github.com/iiab/iiab-factory/tree/master/box/rpi) and then [dd](https://www.linuxnix.com/what-you-should-know-about-linux-dd-command/).  Please see pre-release [screen shots](https://github.com/georgejhunt/iiab-factory/blob/3ver/box/rpi/imager/docs/README.md).  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#827](https://github.com/iiab/iiab/issues/827)
* PREVIEW: Copy Internet-in-a-Box Content Packs to (and from) USB sticks and portable disks.  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#828](https://github.com/iiab/iiab/issues/828).  If a teacher's own ZIM files on a USB stick can be hot-plugged into Internet-in-a-Box, that will be considered too:  [#857](https://github.com/iiab/iiab/issues/857)
* PREVIEW: Your Raspberry Pi's onboard Wi-Fi hotspot can be used to simultaneously get updates from the Internet.  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#697](https://github.com/iiab/iiab/pull/748) [#748](https://github.com/iiab/iiab/pull/748)
* FUTURE: Rapid networking & configuration changes that can't wait ~20min for Ansible.  Coming soon in IIAB 6.7 or 7.0:  [#796](https://github.com/iiab/iiab/pull/796)
* FUTURE: 1-line installers for IIAB that pre-populate [local_vars.yml](wiki.iiab.io/local_vars.yml), auto-reboot intelligently, and automate the torrenting+installing of KA Lite compressed videos (etc) in 7 languages.  Coming soon in IIAB 6.7 or 7.0:  [#872](https://github.com/iiab/iiab/issues/872) [#884](https://github.com/iiab/iiab/issues/884)

### What's Upgraded?

* [1-line installers](http://download.iiab.io/6.6/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 are ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin downloading/installing: whether you want ~6, ~12 or ~20 apps!  Implementers please get to know the commands "[./iiab-install](https://github.com/iiab/iiab/blob/master/iiab-install)" and "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" within directory /opt/iiab/iiab
* Calibre E-Book server [3.27.1+](https://calibre-ebook.com/whats-new) installation procedure is more ruggedized.  Allows teachers to add and delete books using the web interface, edit book metadata, and convert books to other formats like PDF and EPUB.  IIAB's installer now creates the Calibre's default usernames and passwords listed in http://FAQ.IIAB.IO so teachers can begin refining their collection immediately.  PREVIEW: An elegant and friendlier [calibre-web](https://github.com/janeczku/calibre-web) web interface might also be possible for IIAB 6.7  [#816](https://github.com/iiab/iiab/issues/816)
* Media-rich and searchable offline (ZIM) content thanks to an even far better [Kiwix](http://www.kiwix.org/) engine 0.6.0+ (2018-06-20) under the hood, _watch out Google here we come :-)_
* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.5](https://github.com/learningequality/ka-lite/releases/tag/v0.17.5) with installation greatly streamlined.
* Wikipedia's own MediaWiki 1.31.0 LTS is now part of [BIG-sized](http://wiki.iiab.io/local_vars_big.yml) installs of IIAB, for doc collaboration.  You can also install and enable it from [local_vars.yml](http://wiki.iiab.io/local_vars.yml) (typically on Lines 143 and 144).
* Nextcloud is upgraded to [13.0.4+](https://nextcloud.com/changelog/) based on [Nextcloud 13](https://nextcloud.com/blog/nextcloud-13-brings-secure-file-sync-and-collaboration-to-the-next-level/).
* WordPress is upgraded to [4.9.7](https://wordpress.org/news/2018/05/wordpress-4-9-6-privacy-and-maintenance-release/) reinforcing [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) privacy compliance, based on [4.9](https://wordpress.org/news/2017/11/tipton/).  [WordPress 4.9.8](https://wptavern.com/wordpress-4-9-8-to-introduce-try-gutenberg-callout) is expected "2018-07-31".
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.7](https://github.com/Elgg/Elgg/blob/2.3.7/CHANGELOG.md).
* phpMyAdmin is upgraded to [4.8.2](https://www.phpmyadmin.net/news/).
* More comprehensive Offline Docs, onboard your Internet-in-a-Box and available to all in the field, at [http://box/info](http://box/info) &mdash; including instructions on [how to upgrade (or reinstall while offline) your IIAB server apps](http://FAQ.IIAB.IO#Can_I_upgrade_or_reinstall_server_apps.3F) a.k.a. IIAB services.

* Extensive Fixes.  See our [changelog](https://github.com/iiab/iiab/milestone/3?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9:

     curl download.iiab.io/6.6/load.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-06-27 or higher) installed onto a microSD card large enough for content.  Installation usually completes within two hours, if your Internet speed is very fast.  An actual Ethernet cable helps avoid Wi-Fi glitches!  See [download.iiab.io/6.6](http://download.iiab.io/6.6/README.html) for other/faster options.

Finally if you are adventurous, try installing onto CentOS, using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by [CONTRIBUTOR NAMES WILL GO HERE] &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's [quality content collaborations](http://boxing.team) across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* USB memory sticks may need to be [removed and re-inserted](https://github.com/iiab/iiab/issues/329#issuecomment-333330362) into your Internet-in-a-Box before [Teacher Content](http://FAQ.IIAB.IO#Can_teachers_display_their_own_content.3F) appears at http://box/usb e.g. if stick was inserted just prior to a cold boot. [#329](https://github.com/iiab/iiab/issues/329)
* Nextcloud ([http://box/nextcloud](http://box/nextcloud)) logins/logouts are much faster but remain slow. [#401](https://github.com/iiab/iiab/issues/401)
* Set a default locale in your OS in /etc/default/locale (also the "locale" command should show the same, e.g. "C.UTF-8" or "en_US.UTF-8") to avoid language restrictions upon re-installing WordPress.