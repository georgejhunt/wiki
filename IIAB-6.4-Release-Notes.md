Internet-in-a-Box (IIAB) 6.4 ([GitHub](https://github.com/iiab/iiab/milestone/1?closed=1), [Wiki](http://wiki.iiab.io/6.4)) was released on October 5th 2017.

### What's New?

* Search across all your offline (ZIM) content files with an entirely new Kiwix engine under the hood, _watch out Google here we come :-)_
* Support for [Raspbian Stretch](https://www.raspberrypi.org/blog/raspbian-stretch/) and [Debian 9.1](https://www.debian.org/News/2017/20170722) (and likely soon Debian 9.2) anchoring a solid LTS (long-term support) foundation for years to come, in addition to support for [Ubuntu 16.04 LTS](http://releases.ubuntu.com/16.04/) and the new [CentOS 7.4](https://wiki.centos.org/Manuals/ReleaseNotes/CentOS7.1708) sharing the same code base as Red Hat Enterprise Linux 7.4.
* Would you like your IIAB with... [~6](http://wiki.laptop.org/go/IIAB/local_vars_min.yml), [~12](http://wiki.laptop.org/go/IIAB/local_vars.yml) or [~20](http://wiki.laptop.org/go/IIAB/local_vars_big.yml) servers apps?  Now you can choose an app suite &mdash; immediately at the moment you [start downloading](http://download.iiab.io/6.4/rpi/README.html) &mdash; then let it rip as Internet-in-a-Box fully installs itself.
* A complete house cleaning after 2 years, deprecating unmaintained server apps so that installs can proceed far more quickly.  This also brings new, much tighter [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml) system-wide defaults.
* A brand new [Contributors Guide](https://github.com/iiab/iiab/wiki/IIAB-Contributors-Guide) for software developers especially, including our new test automation system thanks [Arky](https://github.com/arky) and [George Hunt](https://github.com/georgejhunt/)!

### What's Upgraded?

* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.3](https://github.com/learningequality/ka-lite/releases) including easy subtitles very popular in developing countries.
* WordPress is upgraded to [4.8.2+](https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/) and now auto-upgrades when your Internet-in-a-Box is online!
* Nextcloud is upgraded to [12.0.3](https://nextcloud.com/changelog/).
* Sugarizer is upgraded to [0.9](http://lists.sugarlabs.org/archive/iaep/2017-September/020080.html).
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.4](https://github.com/Elgg/Elgg/blob/2.3.4/CHANGELOG.md).
* Internet-in-a-Box's own Admin Console (http://box/admin) has been made more resilient.
* [Ansible](https://en.wikipedia.org/wiki/Ansible_(software)) 2.4.x (pre-built PPA or rpm) helps future-proof Internet-in-a-Box configuration management.
* Extraneous red warnings during bootup and during the 1st run of Ansible are gone at last!
* Important [Known Issues in IIAB 6.3](https://github.com/iiab/iiab/wiki/IIAB-6.3-Release-Notes#known-issues) now fixed.

### How do I try it?

TL;DR!  Try our 1-line installer for Raspberry Pi 3:

     curl download.iiab.io/6.4/rpi/load.txt | sudo bash

Be sure your Raspberry Pi 3 is running a recent [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) OS, has a microSD card large enough for content, and is connected to the Internet with an actual Ethernet cable.  Installation usually completes within two hours, if your Internet speed is very fast.  See [download.iiab.io/6.4/rpi](http://download.iiab.io/6.4/rpi/README.html) for other/faster options!

Finally to install onto Ubuntu, Debian or CentOS, use our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; which quickly get you to the most important part &mdash; _where you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Known Issues

* USB memory sticks sometimes need to be [removed and re-inserted](https://github.com/iiab/iiab/issues/329#issuecomment-333330362) into your Internet-in-a-Box before [Teacher Content](http://wiki.laptop.org/go/IIAB/FAQ#Can_teachers_display_their_own_content.3F) appears at http://box/usb (if stick was inserted prior to a cold boot).
* Be sure to set "calibre_install: "False" and "calibre_enabled: False" within [local_vars.yml](http://wiki.laptop.org/go/IIAB/local_vars.yml) before installing IIAB 6.4 on CentOS 7.4