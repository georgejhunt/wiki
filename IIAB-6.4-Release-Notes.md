### _**DRAFT**_

Internet-in-a-Box (IIAB) 6.4 is expected approximately September 2016.

### What's New?

* Search across across offline (ZIM) content files with an entirely new Kiwix engine under the hood, _watch out Google here we come :-)_
* Support for [Raspbian Stretch](https://www.raspberrypi.org/blog/raspbian-stretch/) and [Debian 9.1](https://www.debian.org/News/2017/20170722) guaranteeing a solid LTS (long-term support) foundation for years to come.

### What's Upgraded?

* [KA Lite](http://ka-lite.readthedocs.io/en/latest/installguide/release_notes.html) (LMS for Khan Academy videos & exercises) is upgraded from Version 0.17.0 to [0.17.2](https://github.com/learningequality/ka-lite/releases/tag/v0.17.2) including easy subtitles that are very popular in developing countries.
* Offline Social Network [Elgg](http://learn.elgg.org/en/1.12/) [expected to be] upgraded to 1.12.16 LTS, cleaning up important [errors](https://github.com/Elgg/Elgg/blob/1.12.16/CHANGELOG.md).
* Support [expected] for [CentOS 7.4](https://wiki.centos.org/Manuals/ReleaseNotes/CentOS7.1708) builds on our earlier support for CentOS 7.3 from December 2016.
* Important [Known Issues](https://github.com/iiab/iiab/wiki/IIAB-6.3-Release-Notes#known-issues) from IIAB 6.3 now fixed!

### How do I try it?

TL;DR!  Try a Quick Install on Raspberry Pi 3:

     curl download.iiab.io/6.4/rpi/load.txt | sudo bash

This completes in (about) an hour so long as you're plugged into fast Internet using an actual Ethernet cord.  See http://download.iiab.io/6.4/rpi for even faster options!

To install onto Ubuntu, Debian or CentOS, use our [Do Everything from Scratch](https://github.com/iiab/iiab/wiki/IIAB-Installation#do-everything-from-scratch) full installation instructions, which very quickly get you to the most important part, where you [add content!](https://github.com/iiab/iiab/wiki/IIAB-Installation#add-content)