### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.4 ([GitHub](https://github.com/iiab/iiab/milestone/1)) is expected around late September 2017.

### What's New?

* Search across across offline (ZIM) content files with an entirely new Kiwix engine under the hood, _watch out Google here we come :-)_
* Support for [Raspbian Stretch](https://www.raspberrypi.org/blog/raspbian-stretch/) and [Debian 9.1](https://www.debian.org/News/2017/20170722) and possibly even Debian 9.2, guaranteeing a solid LTS (long-term support) foundation for years to come.
* A complete house-cleaning after 2 years, moving unmaintained server apps into /opt/iiab/iiab/roles/deprecated so that installs can proceed far more quickly.  See the new, much tighter [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml) system-wide defaults.
* Would like your IIAB with... [6](http://wiki.laptop.org/go/IIAB/local_vars_min.yml), [12](http://wiki.laptop.org/go/IIAB/local_vars.yml) or [20](http://wiki.laptop.org/go/IIAB/local_vars_big.yml) servers apps?  Now you can choose an app suite &mdash; immediately at moment you start downloading &mdash; then let it rip as Internet-in-a-Box fully installs itself!

### What's Upgraded?

* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded from Version 0.17.0 to [0.17.2](https://github.com/learningequality/ka-lite/releases/tag/v0.17.2) including easy subtitles very popular in developing countries.  Expected: bug-fix Release 0.17.3 expected in September?
* Offline Social Network [Elgg](http://learn.elgg.org/en/2.3/) upgraded from 1.12.12 to 2.3.3, bringing [extensive improvements](https://github.com/Elgg/Elgg/blob/2.3.3/CHANGELOG.md).
* Support [expected] for [CentOS 7.4](https://wiki.centos.org/Manuals/ReleaseNotes/CentOS7.1708) builds on our earlier support for CentOS 7.3 from December 2016.
* Important [Known Issues](https://github.com/iiab/iiab/wiki/IIAB-6.3-Release-Notes#known-issues) from IIAB 6.3 now fixed!

### How do I try it?

TL;DR!  Try a Quick Install on Raspberry Pi 3:

     curl download.iiab.io/6.4/rpi/load.txt | sudo bash

This completes in (about) an hour so long as you're plugged into fast Internet using an actual Ethernet cable.  And see [download.iiab.io/6.4/rpi](http://download.iiab.io/6.4/rpi) for other/faster options!

To install onto Ubuntu, Debian or CentOS, use our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) full installation instructions, which very quickly get you to the most important part, so you can [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)