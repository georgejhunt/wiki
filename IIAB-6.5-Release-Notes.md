# _**DRAFT**_

Internet-in-a-Box (IIAB) 6.5 ([Wiki](http://wiki.iiab.io/6.5), [GitHub](https://github.com/iiab/iiab/milestone/2)) is expected in February 2018.

### What's New?

* Anybody can now install Internet-in-a-Box (IIAB) with a regular Wi-Fi connection, without the need for an Ethernet cable or router access (after Raspbian/RPi's own [Wi-Fi bugs](https://github.com/iiab/iiab/issues/638) are resolved!)
* Completely overhauled Calibre E-Book server [3.17+](https://calibre-ebook.com/whats-new) on Raspberry Pi: allows adding and deleting of books using the web interface (Internet-in-a-Box installs the very latest Calibre from Kovid Goyal).
* Raspbian, Ubuntu 16.04 and Debian 9 support for [1-line installers](http://download.iiab.io/6.5/rpi/) that are far more efficient, and can quickly recover if Internet is interrupted during installation.  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin downloading/installing, whether you want ~6, ~12 or ~20!  (Implementers please try the new "./iiab-install" and "./runtags" commands in /opt/iiab/iiab, working off our re-organized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) and [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml)).
* Apache proxy of Kiwix (ZIM file usage) empowering community analytics, viewable with AWStats _(documentation growing off [#607](https://github.com/iiab/iiab/issues/607))_.
* Experimental Captive Portal based on nodogsplash, avoiding URL complications for non-Latin communities especially _(documentation growing off [#608](https://github.com/iiab/iiab/issues/608))_.
* Support for large disks, SD cards and USB memory sticks directly out-of-the-box (that are typically NTFS-formatted or exFAT-formatted when purchased) for rapid installation of offline content.
* Experimental support for Ubuntu 17.10, in preparation for Ubuntu 18.04 LTS [expected](https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule) 2017-04-26.
* Compact medical and Wikipedia content in the most popular languages, for schools, clinics and smaller/mobile installations _(coming soon!)_
* Test your IIAB code contributions and Ansible playbooks with [Travis CI](https://github.com/iiab/iiab/wiki/IIAB-Contributors-Guide#testing-your-code-with-travis-ci) continuous integration.

### What's Upgraded?

* Media-rich and searchable offline (ZIM) content thanks to an even far better [Kiwix](http://www.kiwix.org/) engine 0.3.0+ under the hood, _watch out Google here we come :-)_
* Internet-in-a-Box's own Admin Console ([http://box/admin](http://box/admin)) supports downloading new ZIM files (that contain a search index!)  Also supported: traditional ZIM files that are accompanied by an external index, and ZIM files that happen to have no index all.
* Admin Console -> Install Content -> Get ZIM Files from Kiwix is now enhanced by tooltips (small popup windows) helping you drill down to the very best downloadable ZIM content.
* Fixed: Admin Console -> Configure -> Services Enabled's checkboxes ([#378](https://github.com/iiab/iiab/issues/193)).  Fixed: the ability to toggle your IIAB home page to WordPress etc, under Admin Console -> Configure -> Server Portal ([#384](https://github.com/iiab/iiab/issues/384), [#458](https://github.com/iiab/iiab/issues/458)).
* RACHEL modules can now be downloaded/installed directly from [oer2go.org](http://oer2go.org) &mdash; using command line initially _(documentation growing off [#641](https://github.com/iiab/iiab/issues/641))_.
* Sugarizer [0.9](http://sugarizer.org/)'s installation routine is now faster, uses less space, and is more reliable across all OS's ([#193](https://github.com/iiab/iiab/issues/193)).
* Nextcloud is upgraded to [13.0.0](https://nextcloud.com/blog/nextcloud-13-brings-secure-file-sync-and-collaboration-to-the-next-level/).
* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.4](https://github.com/learningequality/ka-lite/releases) and its install routine greatly streamlined.
* WordPress is upgraded to [4.9.4](https://wordpress.org/news/2018/02/wordpress-4-9-4-maintenance-release/) based on [4.9](https://wordpress.org/news/2017/11/tipton/).
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.5](https://github.com/Elgg/Elgg/blob/2.3.5/CHANGELOG.md).
* Moodle is upgraded to [3.1.10](https://docs.moodle.org/dev/Category:Moodle_3.1) LTS.
* phpMyAdmin is upgraded to [4.7.7](https://www.phpmyadmin.net/news/).
* Far more comprehensive Offline Docs, available after you install, at [http://box/info](http://box/info).
* Preliminary documentation [published](http://wiki.laptop.org/go/IIAB/FAQ#Can_I_upgrade_or_reinstall_server_apps.3F) on how to upgrade (or reinstall while offline) your IIAB servers apps a.k.a. IIAB services.
* [Known Issues in IIAB 6.4](https://github.com/iiab/iiab/wiki/IIAB-6.4-Release-Notes#known-issues) are mostly solved.
* Please see our [changelog](https://github.com/iiab/iiab/milestone/2?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3:

     curl download.iiab.io/6.5/rpi/load.txt | sudo bash

Be sure your Raspberry Pi 3 is running a recent [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS, has a microSD card large enough for content, and is connected to the Internet with an actual Ethernet cable.  Installation usually completes within two hours, if your Internet speed is very fast.  See [download.iiab.io/6.5/rpi](http://download.iiab.io/6.5/rpi/README.html) for other/faster options!

Finally to install onto Ubuntu, Debian or CentOS, use our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; which quickly get you to the most important part &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's [quality content collaborations](http://boxing.team) across ALL communities!_

(-: NAMES TO APPEAR HERE :-)

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* Nextcloud ([http://box/nextcloud](http://box/nextcloud)) sometimes takes far too long to login/logout on Raspberry Pi 3 (more than a minute, instead of the usual couple seconds).  If this affects you (typically during the first hours after installation, speeding up later) please help everyone isolate the pattern and root cause, by reviewing & posting to [#401](https://github.com/iiab/iiab/issues/401) so an upstream bug might be filed.
* USB memory sticks sometimes need to be [removed and re-inserted](https://github.com/iiab/iiab/issues/329#issuecomment-333330362) into your Internet-in-a-Box before [Teacher Content](http://wiki.laptop.org/go/IIAB/FAQ#Can_teachers_display_their_own_content.3F) appears at http://box/usb (if stick was inserted just prior to a cold boot).