# _**DRAFT**_

Internet-in-a-Box (IIAB) 6.5 ([Wiki](http://wiki.iiab.io/6.5), [GitHub](https://github.com/iiab/iiab/milestone/2)) is expected around late November 2017.

### What's New?

* Anybody can now install Internet-in-a-Box (IIAB) with a regular Wi-Fi connection, without the need for an Ethernet cable or router access (coming soon!)
* Installation is far more efficient, dramatically more understandable, and quickly recoverable if Internet is interrupted en route!  Thanks to the new "./iiab-install" and "./runtags" commands, working off our re-organized [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) and [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml).  Made possible by Ansible 2.4.1, [#466](https://github.com/iiab/iiab/pull/466) and Jerry Vonau's [#477](https://github.com/iiab/iiab/pull/477).
* Compact medical and Wikipedia content in the most popular languages, for smaller/mobile installations (coming soon!)
* Media-rich and searchable offline (ZIM) content thanks to an even better [Kiwix](http://www.kiwix.org/) engine 0.3.0 under the hood, _watch out Google here we come :-)_
* Test your IIAB code contributions and Ansible playbooks with [Travis CI](https://github.com/iiab/iiab/wiki/IIAB-Contributors-Guide#testing-your-code-with-travis-ci) continuous integration.
* Support for large external hard disks, that are typically NTFS-formatted when they are purchased, facilitating rapid installation of offline content.

### What's Upgraded?

* More reliable [1-line installers](http://download.iiab.io/6.5/rpi/), such that almost anybody can pick their favorite suite of Internet-in-a-Box apps at the very moment they begin downloading/installing.
* Far more comprehensive Offline Docs, available after you install at [http://box/info](http://box/info).
* Sugarizer [0.9](http://sugarizer.org/)'s installation routine is now faster, uses less space, and is more reliable across all OS's ([#193](https://github.com/iiab/iiab/issues/193)).
* Nextcloud is upgraded to [12.0.4](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule) or [13.0.0](https://github.com/nextcloud/server/milestones) (coming soon!)
* WordPress is upgraded to [4.9](https://make.wordpress.org/core/tag/4-9/) (coming soon!)
* Moodle is upgraded to [3.1.9](https://docs.moodle.org/dev/Category:Moodle_3.1) LTS (coming soon!)
* phpMyAdmin is upgraded to [4.7.5](https://www.phpmyadmin.net/news/).
* Internet-in-a-Box's own Admin Console ([http://box/admin](http://box/admin)) checkboxes ([#378](https://github.com/iiab/iiab/issues/193)) & home page management are greatly improved ([#384](https://github.com/iiab/iiab/issues/384)) (coming soon!)
* Important [Known Issues in IIAB 6.4](https://github.com/iiab/iiab/wiki/IIAB-6.4-Release-Notes#known-issues) mostly solved (coming soon!)
* Please see our [changelog](https://github.com/iiab/iiab/milestone/2?closed=1) of accomplishments!

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3:

     curl download.iiab.io/6.5/rpi/load.txt | sudo bash

Be sure your Raspberry Pi 3 is running a recent [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS, has a microSD card large enough for content, and is connected to the Internet with an actual Ethernet cable.  Installation usually completes within two hours, if your Internet speed is very fast.  See [download.iiab.io/6.5/rpi](http://download.iiab.io/6.5/rpi/README.html) for other/faster options!

Finally to install onto Ubuntu, Debian or CentOS, use our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; which quickly get you to the most important part &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's [quality content collaborations](http://boxing.team) across ALL communities!_

Join our Monday/Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)