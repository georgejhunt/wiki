# _**DRAFT**_

Internet-in-a-Box (IIAB) 6.4 ([GitHub](https://github.com/iiab/iiab/milestone/1), [Wiki](http://wiki.iiab.io/6.4)) is expected in early October 2017.

### What's New?

* Search across across all your offline (ZIM) content files with an entirely new Kiwix engine under the hood, _watch out Google here we come :-)_
* Support for [Raspbian Stretch](https://www.raspberrypi.org/blog/raspbian-stretch/) and [Debian 9.1](https://www.debian.org/News/2017/20170722) (and possibly soon Debian 9.2) anchoring a solid LTS (long-term support) foundation for years to come.
* Would you like your IIAB with... [6](http://wiki.laptop.org/go/IIAB/local_vars_min.yml), [12](http://wiki.laptop.org/go/IIAB/local_vars.yml) or [20](http://wiki.laptop.org/go/IIAB/local_vars_big.yml) servers apps?  Now you can choose an app suite &mdash; immediately at the moment you [start downloading](http://download.iiab.io/6.4/rpi/) &mdash; then let it rip as Internet-in-a-Box fully installs itself!
* A complete house cleaning after 2 years, deprecating unmaintained server apps so that installs can proceed far more quickly.  This also brings new, much tighter [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml) system-wide defaults.

### What's Upgraded?

* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded to [0.17.3](https://github.com/learningequality/ka-lite/releases) including easy subtitles very popular in developing countries.
* WordPress is upgraded to [4.8.2](https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/) (auto-upgrades when your Internet-in-a-Box is online!)
* Nextcloud is upgraded to [12.0.3](https://nextcloud.com/changelog/).
* Sugarizer is upgraded to [0.9](http://lists.sugarlabs.org/archive/iaep/2017-September/020080.html).
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) is upgraded to [2.3.4](https://github.com/Elgg/Elgg/blob/2.3.4/CHANGELOG.md).
* [Ansible](https://en.wikipedia.org/wiki/Ansible_(software)) 2.4.0 (pre-built PPA or rpm) helps future-proof Internet-in-a-Box configuration management.
* Support for [CentOS 7.4](https://wiki.centos.org/Manuals/ReleaseNotes/CentOS7.1708) builds on our earlier support for CentOS 7.3 from December 2016.
* Important [Known Issues in IIAB 6.3](https://github.com/iiab/iiab/wiki/IIAB-6.3-Release-Notes#known-issues) now fixed!

### How do I try it?

TL;DR!  Try a Quick Install on Raspberry Pi 3:

     curl download.iiab.io/6.4/rpi/load.txt | sudo bash

This completes in (about) an hour so long as you're plugged into fast Internet using an actual Ethernet cable.  Also see [download.iiab.io/6.4/rpi](http://download.iiab.io/6.4/rpi) for other/faster options!

Finally, to install onto Ubuntu, Debian or CentOS, use our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) install instructions &mdash; which quickly get you to the most important part &mdash; _whereupon you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)_

### Known Issues

* Nextcloud logins take 1-to-2 min on Raspberry Pi 3.