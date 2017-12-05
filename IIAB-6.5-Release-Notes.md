# _**DRAFT**_

Internet-in-a-Box (IIAB) 6.5 ([Wiki](http://wiki.iiab.io/6.5), [GitHub](https://github.com/iiab/iiab/milestone/2)) is expected in early December 2017.

### What's New?

* Completely overhauled Calibre E-Book server [3.13+](https://calibre-ebook.com/whats-new) on Raspberry Pi!  (Internet-in-a-Box installs the very latest from Kovid Goyal)
* Anybody can now install Internet-in-a-Box (IIAB) with a regular Wi-Fi connection, without the need for an Ethernet cable or router access _(coming soon!)_
* Compact medical and Wikipedia content in the most popular languages, for smaller/mobile installations _(coming soon!)_
* Raspbian, Ubuntu 16.04 and Debian 9 support for [1-line installers](http://download.iiab.io/6.5/rpi/) that are far more efficient, and can quickly recover if Internet is interrupted during installation.  Pick your favorite suite of Internet-in-a-Box apps the very moment you begin downloading/installing!  (Implementers please try the new "./iiab-install" and "./runtags" commands in /opt/iiab/iiab, working off our re-organized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) and [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml)).
* Experimental support for Ubuntu 17.10, in preparation for Ubuntu 18.04 LTS arriving in April.
* Experimental captive portal based on nodogsplash [#412](https://github.com/iiab/iiab/issues/412) _(coming soon!)_
* Support for large disks, SD cards and USB memory sticks directly out-of-the-box (that are typically NTFS-formatted or exFAT-formatted when purchased) facilitating rapid installation of offline content.
* Test your IIAB code contributions and Ansible playbooks with [Travis CI](https://github.com/iiab/iiab/wiki/IIAB-Contributors-Guide#testing-your-code-with-travis-ci) continuous integration.

### What's Upgraded?

* Media-rich and searchable offline (ZIM) content thanks to an even far better [Kiwix](http://www.kiwix.org/) engine 0.3.0+ under the hood, _watch out Google here we come :-)_
* Internet-in-a-Box's own Admin Console ([http://box/admin](http://box/admin)) supports downloading new ZIM files (that contain a search index!)  Also supported: traditional ZIM files that are accompanied by an external index, and ZIM files that happen to have no index all.
*  Admin Console -> Install Content -> Get ZIM Files from Kiwix is now enhanced by tooltips (small popup windows) helping you drill down to the very best downloadable ZIM content.
* Fixed: Admin Console -> Configure -> Services Enabled's checkboxes ([#378](https://github.com/iiab/iiab/issues/193)).  Fixed: the ability to toggle your IIAB home page to WordPress etc, under Admin Console -> Configure -> Server Portal ([#384](https://github.com/iiab/iiab/issues/384), [#458](https://github.com/iiab/iiab/issues/458)).  
* Sugarizer [0.9](http://sugarizer.org/)'s installation routine is now faster, uses less space, and is more reliable across all OS's ([#193](https://github.com/iiab/iiab/issues/193)).
* Nextcloud is upgraded to [12.0.4](https://nextcloud.com/blog/nextcloud-12.0.4-is-here-time-to-upgrade/) and [13.0.0](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule) is coming soon.
* WordPress is upgraded to [4.9.1](https://wordpress.org/news/2017/11/tipton/).
* Moodle is upgraded to [3.1.9](https://docs.moodle.org/dev/Category:Moodle_3.1) LTS.
* phpMyAdmin is upgraded to [4.7.6](https://www.phpmyadmin.net/news/).
* Far more comprehensive Offline Docs, available after you install, at [http://box/info](http://box/info).
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