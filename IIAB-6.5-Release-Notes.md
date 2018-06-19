Internet-in-a-Box (IIAB) 6.5 was released on May 24th, 2018 and updated on June 10th, 2018 ([Wiki](http://wiki.iiab.io/6.5), [GitHub](https://github.com/iiab/iiab/milestone/2)).

### What's New?

* [1-line installers](http://download.iiab.io/6.5/) for Raspbian Stretch, Ubuntu 18.04 LTS and Debian 9 are now far more efficient &mdash; and can quickly recover if Internet is interrupted during installation.  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin downloading/installing: whether you want ~6, ~12 or ~20 apps!  Implementers check out the new "./iiab-install" and "./runrole" (formerly "./runtags") commands in /opt/iiab/iiab &mdash; working off our re-organized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) and [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml).
* Anybody can now [install Internet-in-a-Box over regular WiFi](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch).  On Raspberry Pi, run `raspi-config` to connect to your home's WiFi SSID and password prior to installing IIAB.  Then run `iiab-hotspot-on` after IIAB installation is complete!  Or: accelerate your install if you have an Ethernet cable to live Internet (physical cables are almost always more reliable than radio waves).  IIAB 6.6 Preview: on Raspberry Pis, we hope to support WiFi-as-client *simultaneous* with WiFi-as-hotspot, streamlining updates!  [#697](https://github.com/iiab/iiab/pull/697) [#748](https://github.com/iiab/iiab/pull/748)
* Click to download and install [ZIM files](https://github.com/iiab/iiab/wiki/IIAB-Installation#zim-files) or any [OER2GO (RACHEL)](https://github.com/iiab/iiab/wiki/IIAB-Installation#oer2go-rachel-modules) module.  Remove any of these using http://box/admin -> Install Content -> Remove Files to clear up space!  Tooltips (small popup windows) now help you drill down and verify content details while [adding](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content) or [removing](https://github.com/iiab/iiab/wiki/IIAB-Installation#remove-content) such content packs.  NEW: Works with the new ZIM files (these contain an integrated search index), traditional ZIM files that are accompanied by an external index, and also ZIM files that happen to have no index all.
* Completely overhauled Calibre E-Book server [3.25+](https://calibre-ebook.com/whats-new).  Allows teachers to add and delete books using the web interface, as well as editing book metadata.
* Automounting of larger USB memory sticks, SD cards and portable disks (these are typically exFAT-formatted or NTFS-formatted when purchased).  Makes it easy to (1) install & redistribute content while offline, and (2) [empowers teachers to instantly display their own USB stick content](http://wiki.laptop.org/go/IIAB/FAQ#Can_teachers_display_their_own_content.3F) to students via http://box/usb
* Usage statistics of ZIM files (for teachers especially) are viewable with AWStats on your IIAB server at http://box/awstats/awstats.pl ([instructions](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_view_usage_statistics.3F)).  We do this using an Apache proxy (http://box/kiwix/ instead of the usual http://box:3000) hoping to empower teachers to understand their own student community analytics.
* Wikipedia's own MediaWiki 1.30.0 is now part of IIAB, if you enable it in [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) (typically on Lines 143 and 144) for doc collaboration.
* Experimental Captive Portal based on nodogsplash, reducing users' URL frustrations for non-Latin communities especially.  [#608](https://github.com/iiab/iiab/issues/608)
* Code is dramatically more approachable by developers and implementers.  Preview: Test your IIAB code contributions and Ansible playbooks with [Travis CI](https://github.com/iiab/iiab/wiki/IIAB-Contributors-Guide#testing-your-code-with-travis-ci) continuous integration.

### What's Upgraded?

* Far more comprehensive Offline Docs, onboard your Internet-in-a-Box and available to all in the field, at [http://box/info](http://box/info) &mdash; including instructions on [how to upgrade (or reinstall while offline) your IIAB server apps](http://wiki.laptop.org/go/IIAB/FAQ#Can_I_upgrade_or_reinstall_server_apps.3F) a.k.a. IIAB services.
* Media-rich and searchable offline (ZIM) content thanks to an even far better [Kiwix](http://www.kiwix.org/) engine 0.5.0+ (2018-05-24) under the hood, _watch out Google here we come :-)_
* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.4](https://github.com/learningequality/ka-lite/releases/tag/v0.17.4) with installation greatly streamlined.
* Sugarizer [0.9](https://groups.google.com/forum/m/#!topic/unleashkids/YzXPMgp28vY) installs faster, uses less space, and is more reliable across all OS's.  Preview: Sugarizer [1.0](https://groups.google.com/forum/m/#!topic/unleashkids/jnJHfjbhPPA) is a major forthcoming upgrade.  [#814](https://github.com/iiab/iiab/pull/814)
* Nextcloud is upgraded to [13.0.3+](https://nextcloud.com/blog/nextcloud-13.0.3-and-12.0.8-available/) based on [Nextcloud 13](https://nextcloud.com/blog/nextcloud-13-brings-secure-file-sync-and-collaboration-to-the-next-level/).
* WordPress is upgraded to [4.9.6](https://wordpress.org/news/2018/05/wordpress-4-9-6-privacy-and-maintenance-release/) bringing [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) privacy compliance, based on [4.9](https://wordpress.org/news/2017/11/tipton/).
* Moodle is upgraded to [3.5 LTS](https://docs.moodle.org/dev/Moodle_3.5_release_notes) for privacy, better quizzes, speed, messaging integration and modern usability ([preview](https://www.moodlenews.com/2018/privacy-better-quizzes-faster-and-modern-the-latest-scoop-on-moodle-3-5/), [new features](https://docs.moodle.org/35/en/New_features)).
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.7](https://github.com/Elgg/Elgg/blob/2.3.7/CHANGELOG.md).
* DokuWiki is upgraded to [2018-04-22a "Greebo"](https://www.dokuwiki.org/changes#release_2018-04-22_release_greebo).
* phpMyAdmin is upgraded to [4.8.1](https://www.phpmyadmin.net/news/).
* Extensive Fixes, just to name a few: Admin Console -> Configure -> Services Enabled's checkboxes ([#378](https://github.com/iiab/iiab/issues/193)).  Fixed: the ability to toggle your IIAB home page to WordPress etc, under Admin Console -> Configure -> Server Portal ([#384](https://github.com/iiab/iiab/issues/384), [#458](https://github.com/iiab/iiab/issues/458)).  See our [changelog](https://github.com/iiab/iiab/milestone/2?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3 (or 3 B+), Ubuntu 18.04 LTS or Debian 9:

     curl download.iiab.io/6.5/load.txt | sudo bash

On Raspberry Pi, you'll want the latest [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS (2018-04-18 or higher) installed onto a microSD card large enough for content.  Installation usually completes within two hours, if your Internet speed is very fast.  An actual Ethernet cable helps avoid WiwiFi glitches!  See [download.iiab.io/6.5](http://download.iiab.io/6.5/README.html) for other/faster options.

Finally try installing onto CentOS, using our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; getting you to the most important step &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.  Building on this software and designs contributed by Jerry Vonau, Tim Moody, George Hunt, Adam Holt, Josh Dennis, Joshua Kanani, Reno McKenzie, Blondel Mondésir, Avni Khatri, Arky R., Anish Mangal, Carlos Garcia &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's [quality content collaborations](http://boxing.team) across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* USB memory sticks may need to be [removed and re-inserted](https://github.com/iiab/iiab/issues/329#issuecomment-333330362) into your Internet-in-a-Box before [Teacher Content](http://wiki.laptop.org/go/IIAB/FAQ#Can_teachers_display_their_own_content.3F) appears at http://box/usb e.g. if stick was inserted just prior to a cold boot. [#329](https://github.com/iiab/iiab/issues/329)
* Nextcloud ([http://box/nextcloud](http://box/nextcloud)) logins/logouts are much faster but remain slow. [#401](https://github.com/iiab/iiab/issues/401)
* Set a default locale in your OS in /etc/default/locale (also the "locale" command should show the same, e.g. "C.UTF-8" or "en_US.UTF-8") to avoid language restrictions upon re-installing WordPress.