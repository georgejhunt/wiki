### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.6 incorporates an extensive amount of teacher feedback from [IIAB 6.5](https://github.com/iiab/iiab/wiki/IIAB-6.5-Release-Notes), and will be released in August ([Wiki](http://wiki.iiab.io/6.6), [GitHub](https://github.com/iiab/iiab/milestone/3)) in service of DIY digital libraries everywhere.

FOCUS: Teachers’ + (field) Techs’ + Testers’ immediate needs (<a href=https://github.com/iiab/iiab/pull/840>checklist</a>).

CLARIF: Larger architectural improvements will be deferred to [IIAB 6.7](http://wiki.iiab.io/6.7) or [IIAB 7.0](https://github.com/iiab/iiab/milestone/5).

_TODAY: Consider installing a <a href=http://download.iiab.io/6.6>pre-release of IIAB 6.6</a> !_

### What's New? (TENTATIVE)

* Experimental support for [Kolibri 0.10.2+](https://blog.learningequality.org/kolibri-v0-10-is-released-4e673398f116) ([background](https://blog.learningequality.org/startwithkolibri-58227e98dde), [changelog](https://github.com/learningequality/kolibri/blob/develop/CHANGELOG.rst)) which is similar to [KA Lite](https://learningequality.org/ka-lite/) but offers many more curriculum design tools beyond Khan Academy, to create, remix and refine offline content packs:  [#841](https://github.com/iiab/iiab/issues/841#issuecomment-405767755)
* [Sugarizer 1.0.1](http://sugarizer.org) is a "kids construct" learning environment originally from One Laptop Per Child, with easy accounts for kids to save their work.  Sugarizer 1.x is a major change from earlier versions:  [#798](https://github.com/iiab/iiab/issues/798#issuecomment-405609004), [PR #888](https://github.com/iiab/iiab/pull/888#issuecomment-404370082), [#974](https://github.com/iiab/iiab/issues/974)
* OpenStreetMap regional maps packs are now almost 10X smaller, offer far more local detail, are more up-to-date, and are easier to install &mdash; thanks to regularly published vector-based tilesets &mdash; instead of the older bitmap tiles:
  * 10 levels of zoom are included for the entire world, including ocean floors.
  * Locate any of 127,654 cities/settlement worldwide, whose population is larger than 1000.
  * Other regions can easily be installed from [OpenMapTiles.com](https://openmaptiles.com/downloads/planet/) if you want 14 levels of zoom, with overzoom to level 18+ (including building outlines in many cases!)  See ["How do I add zoomable maps for my region?"](http://FAQ.IIAB.IO#How_do_I_add_zoomable_maps_for_my_region.3F) in http://FAQ.IIAB.IO and our detailed [README](https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/README.md).
  * Online samples are viewable for the [San Francisco Bay Area](http://medbox.iiab.me/modules/en-osm-omt-min/) (includes this [109MB regional dataset](https://openmaptiles.com/downloads/north-america/us/california/san-francisco-bay/)) or choose [Central America & the Caribbean](http://medbox.iiab.me/modules/en-osm-omt-central-am/) (includes this [1.1-1.8 GB regional dataset](https://openmaptiles.com/downloads/central-america/)).  [#877](https://github.com/iiab/iiab/issues/877#issuecomment-405935272)
* PREVIEW: Easy backup, duplication and shrinking of Internet-in-a-Box (IIAB) microSD cards using [IMAGER](http://download.iiab.io/packages/imager/).  Allows teachers in the field to copy from any microSD to any other microSD that's big enough.  These are teachers who cannot realistically use Linux command-line tools to [truncate (AKA shrink, or minify)](https://github.com/iiab/iiab-factory/tree/master/box/rpi) and then [dd](https://www.linuxnix.com/what-you-should-know-about-linux-dd-command/).  Please see pre-release [screen shots](https://github.com/iiab/iiab-factory/blob/master/box/rpi/imager/docs/README.md).  Not yet landed but coming soon in IIAB 6.6 or 6.7:  [#827](https://github.com/iiab/iiab/issues/827)

### What's Upgraded? (TENTATIVE)

* Internet-in-a-Box's [1-line installer](http://download.iiab.io/6.6/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 is ruggedized and more efficient (and can quickly recover if Internet is interrupted during your IIAB installation).  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin: whether you want ~6, ~12 or ~20 apps!  Implementers please read http://FAQ.IIAB.IO to get to know [/etc/iiab/local_vars.yml](http://wiki.iiab.io/local_vars.yml) — as well as the commands "[./iiab-install](https://github.com/iiab/iiab/blob/master/iiab-install)" and "[./runrole](https://github.com/iiab/iiab/blob/master/runrole)" within IIAB's main directory (/opt/iiab/iiab).
  * New, more convenient location for your IIAB installation settings: [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml).  Regional communities can now instantly re-use their favorite/custom IIAB configurations (much like IIAB microSD card cloning, also coming soon!)  *Simply drop this file in place* (/etc/iiab/local_vars.yml) and then start your IIAB install on any fresh/new machine &mdash; next time you run `curl download.iiab.io/6.6/install.txt | sudo bash`
  * You can now RE-run "curl download.iiab.io/6.6/install.txt | sudo bash" (after Internet glitches, or on a brand-new machine if you copied someone else's /etc/iiab/local_vars.yml) thanks to IIAB's new unified installer.
  * Explanations in context as IIAB is installing, and major improvements in Ansible code readability (IIAB's [Ansible playbooks](https://github.com/iiab/iiab/tree/master/roles) are far more readable, with modern indentation, instead of cramming too many things into 1 line).  [Ansible 2.6](https://docs.ansible.com/ansible/2.6/porting_guides/porting_guide_2.6.html) helps future-proof Internet-in-a-Box configuration management.
  * OpenVPN remote support is beefed up: variable openvpn_handle can now be pre-specified in [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml), before it's auto-saved to /etc/iiab/openvpn_handle:  [#995](https://github.com/iiab/iiab/issues/995), [PR #1000](https://github.com/iiab/iiab/pull/1000)
  * Experimental support for [Debian 10 "Buster"](https://www.debian.org/devel/debian-installer/) is included, in advance of Debian 10's release in 2019.  [Debian "Sid"](http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/current/amd64/iso-cd/) (AKA Debian's "unstable" bleeding-edge branch) might also work.
* Calibre E-Book server [3.30+](https://calibre-ebook.com/whats-new) installation procedure is more ruggedized.  Allows teachers to add and delete books using the web interface, edit book metadata, and convert books to other formats like PDF and EPUB.  IIAB's installer now creates the Calibre's default usernames and passwords listed in http://FAQ.IIAB.IO so teachers can begin refining their collection immediately.
  * PREVIEW: An elegant and friendlier [calibre-web](https://github.com/janeczku/calibre-web) web interface has not yet landed but is coming soon in IIAB 6.6 or 6.7:  [#816](https://github.com/iiab/iiab/issues/816)
* Media-rich and searchable offline (ZIM) content thanks to an even far better [Kiwix](http://www.kiwix.org/) engine 0.6.0 (2018-06-20) under the hood, _watch out Google here we come :-)_
* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.5](https://github.com/learningequality/ka-lite/releases/tag/v0.17.5) with installation greatly streamlined.
* Wikipedia's own MediaWiki [1.31.0 LTS](https://www.mediawiki.org/wiki/MediaWiki_1.31) is now part of [BIG-sized](http://wiki.iiab.io/local_vars_big.yml) installs of IIAB, for doc collaboration.  You can also install and enable it from [local_vars.yml](http://wiki.iiab.io/local_vars.yml) (typically on Lines 143 and 144).
* Nextcloud is upgraded to [13.0.6](https://nextcloud.com/blog/) ([changelog](https://nextcloud.com/changelog/)) based on [Nextcloud 13](https://nextcloud.com/blog/nextcloud-13-brings-secure-file-sync-and-collaboration-to-the-next-level/).
* WordPress is upgraded to [4.9.8](https://wordpress.org/news/2018/08/wordpress-4-9-8-maintenance-release/) including “Try Gutenberg” visual/block editor preview.  Reinforces [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) privacy compliance, based on WordPress [4.9](https://wordpress.org/news/2017/11/tipton/).
* Moodle is upgraded to [3.5.1+ LTS](https://docs.moodle.org/dev/Moodle_3.5.1_release_notes) based on [3.5 LTS](https://docs.moodle.org/dev/Moodle_3.5_release_notes) for privacy, better quizzes, speed, messaging integration and modern usability ([preview](https://www.moodlenews.com/2018/privacy-better-quizzes-faster-and-modern-the-latest-scoop-on-moodle-3-5/), [new features](https://docs.moodle.org/35/en/New_features)).
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.8](https://github.com/Elgg/Elgg/blob/2.3.8/CHANGELOG.md).
* phpMyAdmin is upgraded to [4.8.3](https://www.phpmyadmin.net/news/).
* More comprehensive Offline Docs, onboard your Internet-in-a-Box and available to all in the field, at [http://box/info](http://box/info) &mdash; including instructions on [how to upgrade (or reinstall while offline) your IIAB server apps](http://FAQ.IIAB.IO#Can_I_upgrade_or_reinstall_server_apps.3F) a.k.a. IIAB services.
* Extensive Fixes.  See our [changelog](https://github.com/iiab/iiab/milestone/3?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9:

     curl download.iiab.io/6.6/install.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-06-27 or higher) installed onto a microSD card large enough for all your content.  Installation usually completes within two hours, if your Internet speed is very fast.  An actual Ethernet cable greatly helps avoid Wi-Fi glitches!  See [download.iiab.io/6.6](http://download.iiab.io/6.6/) for speed and security tips to hit the ground running.

Finally if you're adventurous, try installing onto [another Linux](https://github.com/iiab/iiab/wiki/IIAB-Platforms), using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by [CONTRIBUTOR NAMES GO HERE] &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's quality content collaborations across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* RACHEL's OER2GO catalog does not show sample modules and cannot be refreshed due to regression(s) on their server: [#853](https://github.com/iiab/iiab/issues/853#issuecomment-412202168)
* Some short/memorizable URL's like http://box/kolibri do not yet work.  Use [http://box:8009](http://box:8009) in the interim:  [#923](https://github.com/iiab/iiab/issues/923)
* Raspberry Pi's internal Wi-Fi hotspot very occasionally fails to provide IP addresses, when Ethernet ISN'T plugged in? 
 [#989](https://github.com/iiab/iiab/issues/989)
* Raspberry Pi's internal Wi-Fi hotspot very occasionally fails within an hour of booting, when Ethernet IS plugged in?  [#926](https://github.com/iiab/iiab/issues/926)
* Calibre 3.29 (like 3.27.1, 3.24.x and 3.25) prevents IIAB microSD's from booting in Raspberry Pi Zero W.  Those who rely on RPi Zero W, please remember to turn off Calibre in /etc/iiab/local_vars.yml prior to installing of IIAB:  [#952](https://github.com/iiab/iiab/issues/952)
* USB memory sticks may need to be [removed and re-inserted](https://github.com/iiab/iiab/issues/329#issuecomment-333330362) into your Internet-in-a-Box before [Teacher Content](http://FAQ.IIAB.IO#Can_teachers_display_their_own_content.3F) appears at http://box/usb e.g. if stick was inserted just prior to a cold boot:  [#329](https://github.com/iiab/iiab/issues/329)
* Nextcloud ([http://box/nextcloud](http://box/nextcloud)) logins/logouts are much faster but remain slow:  [#401](https://github.com/iiab/iiab/issues/401)
* Set a default locale in your OS in /etc/default/locale (also the "locale" command and $LANG environment variable should show the same, e.g. "C.UTF-8" or "en_US.UTF-8") to avoid language restrictions upon re-installing WordPress.