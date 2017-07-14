Internet-in-a-Box (IIAB) 6.3 was released July 13, 2017, including dramatic improvements for educator/implementer communities &mdash; like an entirely new Kiwix engine, fixing the notorious [Chrome bug](https://github.com/kiwix/tools/issues/1) &mdash; while also better supporting full-text searching across old ZIM files *and* new ZIM files both.

Pre-release versions of IIAB 6.3 have already been brought to Ghana, Dominican Republic, Haiti, Nicaragua and Malaysia &mdash; while implementation work is currently ongoing for Lebanon and Guatemala.  We're very honored that IIAB 6.3 is increasingly used in medical education (post-secondary and clinical contexts) as well as for children's primary and secondary education!

IIAB 6.3 now runs on Ubuntu, as well as Raspbian (on Raspberry Pi) and several other Linux distributions like CentOS and Debian.  Read [IIAB Platforms](https://github.com/iiab/iiab/wiki/IIAB-Platforms) and [FAQ.IIAB.IO](http://wiki.laptop.org/go/IIAB/FAQ) as our community documentation is beefed up for educators and implementers/operators, now accessible offline (http://box/info) and online (https://github.com/iiab/iiab/wiki) both!  Internally, Internet-in-a-Box Tech Docs underwent significant revision as they moved from github.com/xsce to github.com/iiab.

Likewise our code (software) made the big move from [github.com/xsce](https://github.com/xsce) to [github.com/iiab](http://github.com/iiab) honoring our new name (Internet in a Box) with extensive internal "iiab" naming changes put in place (to avoid confusion with legacy "xsce" and "xs" naming conventions).  In support of a new generation of contributors jumping in to engage, as we're about to enter our 2nd decade!

Among the suite of server apps you can choose from, a new version of WordPress (4.8) is offered.  IIAB 6.3 also brings a much-anticipated transition from ownCloud to [Nextcloud](https://nextcloud.com/) strongly backed by free and open-source communities.  For medical and low-electricity environments, IIAB 6.3 greatly accelerates boot and shutdown times &mdash; while also providing a friendlier "single-click to power off" button for those requiring that.

IIAB 6.3 dramatically steps up DIY implementers' ability to quickly arrange their own portal/menus of popular Content Packs, thanks to enhanced [Dynamic Menuing](https://github.com/iiab/iiab/wiki/IIAB-Menuing) (instead of hand-coding index.html).  Also OpenStreetMap has been made customizable to essentially every educational context, thanks to a [new utility](https://github.com/georgejhunt/iiab-factory/blob/subset-osm/content/subset-osm/README.md) that arranges zoomable offline map data for those regions that are truly relevant and required.

Give it a shot!  Installing onto [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) on Raspberry Pi 3 is as easy as running this 1-line command, which completes in (about) an hour:

     curl download.iiab.io/6.3/rpi/load.txt | sudo bash

For more details, see [wiki.iiab.io/6.3](http://wiki.laptop.org/go/IIAB/6.3) and [FAQ.IIAB.IO](http://wiki.laptop.org/go/IIAB/FAQ).  To install onto laptops or larger servers, please also explore [download.iiab.io/6.3](http://download.iiab.io/6.3).

_We're thrilled that new countries and communities keep getting involved &mdash; supporting each other along the way &mdash; many of which are joining us at the http://OFF.NETWORK Hackathon August 13-18, 2017 in Potsdam, NY.  Please don't hesitate to [get in touch](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_best_places_for_community_support.3F) as you too build your very own community digital library!_

IIAB Development Team<br>
http://IIAB.io