<!--TBA: Expected in Q1 2020.>

<!--For now, please see the [IIAB 7.1 Release Notes](https://github.com/iiab/iiab/wiki/IIAB-7.1-Release-Notes).-->

### _DRAFT_

[Internet-in-a-Box (IIAB)](http://internet-in-a-box.org) version 7.1 will build upon [IIAB 7.0](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes), to be released in April 2020 ([Roadmap Ideas](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes#what-might-future-versions-bring), [GitHub Milestone](https://github.com/iiab/iiab/milestone/6), [Wiki](http://wiki.laptop.org/go/IIAB/7.1)) in service of DIY digital libraries for schools, clinics and communities across all corners of the planet.

See our Frequently Asked Questions ([FAQ.IIAB.IO](http://wiki.laptop.org/go/IIAB/FAQ)) and consider installing a pre-release today:

<p align="center">
  <b><a href=http://download.iiab.io>download.iiab.io</a></b>
  <!--[download.iiab.io](http://download.iiab.io)-->
</p>

Please [join us in making this major release happen](http://internet-in-a-box.org/pages/contributing.html), Thank You!

### About

Internet-in-a-Box brings the [Internet's crown jewels](http://internet-in-a-box.org/#quality-content) and the very best of the World’s Free Knowledge (Wikipedia, Khan Academy, OpenStreetMap, E-Books, etc) to those who are burning for learning — but just happen to be offline.

Use <b>drag-and-drop</b> to customize this "learning hotspot" with local gems too — tailored to the needs of your school, your library, your prison, your region and/or your very own family!

Why not build your own [LIBRARY OF ALEXANDRIA](https://www.youtube.com/channel/UC0cBGCxr_WPBPa3IqPVEe3g) with a $35 Raspberry Pi 4 computer, starting today?

### What's New?

- [Python 3.x](https://python-release-cycle.glitch.me/) instead of [Python 2.7](https://pythonclock.org/), putting Internet-in-a-Box (IIAB) on a whole new foundation for a new decade  <sub><sub>[#1810](https://github.com/iiab/iiab/issues/1810)</sub></sub>
- [NGINX](https://github.com/iiab/iiab/tree/master/roles/nginx#transition-to-nginx) alongside Apache, greatly modernizing IIAB's web server engine and associated underlying infrastructure.  <sub><sub>[#224](https://github.com/iiab/iiab/issues/224)</sub></sub>
- [Captive Portal](http://wiki.laptop.org/go/IIAB/FAQ#Captive_Portal_Administration:_What_tips_.26_tricks_exist.3F) that actually works well on substantially more client devices and browsers!  <sub><sub>[PR #2185](https://github.com/iiab/iiab/pull/2185)</sub></sub>
- Instant submission of Content Pack descriptions/logos for your IIAB home page, so non-technical implementers/educators around the planet can rapidly & efficiently circulate ["menu item definitions"](https://github.com/iiab/iiab/wiki/IIAB-Menuing) &mdash; _putting community action into high gear._  <sub><sub>[#1831](https://github.com/iiab/iiab/issues/1831)</sub></sub>
- Clone your entire Internet-in-a-Box (IIAB) e.g. to an external microSD card, using IIAB's Admin Consol: http://box.lan/admin -> Install Content -> ? <sub><sub>[#2268](https://github.com/iiab/iiab/issues/2268)</sub></sub>
- Coming Soon: [Cham](https://github.com/eka-foundation/cham) is a lightweight live video streaming platform with adaptive bitrates for IIAB.  <sub><sub>[PR #1743](https://github.com/iiab/iiab/pull/1743)</sub></sub>
- Auto-validation of the most important variables in your [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F) configuration file, to catch simple mistakes or typos, and alert you promptly near the very beginning of IIAB's installation.  <sub><sub>[PR #2180](https://github.com/iiab/iiab/pull/2180)</sub></sub>

### What's Upgraded?

- [Kolibri 0.13.1+](https://medium.com/kolibri-releases/kolibri-v0-13-is-here-4ac99259367a) ([changelog](https://github.com/learningequality/kolibri/releases)) with URL _box/kolibri_
- [Nextcloud 18.0.2+](https://nextcloud.com/blog/) ([changelog](https://nextcloud.com/changelog/#latest18)) with URL _box/nextcloud_
- [Calibre-Web 0.6.6](https://github.com/janeczku/calibre-web#about) ([changelog](https://github.com/janeczku/calibre-web/releases)) with customizable URL's _box/books, box/libros, box/livres_
- [Calibre 4.13+](https://calibre-ebook.com/whats-new) (3.39.1+ on Raspberry Pi) with URL _box:8080_
- [Lokole 0.5.11+](https://github.com/iiab/iiab/tree/master/roles/lokole#lokole-readme) ([changelog](https://github.com/ascoderu/opwen-webapp/releases)) email for rural communities, students and teachers, with URL _box/lokole_
- [Moodle 3.8.2+](https://docs.moodle.org/dev/Moodle_3.8.1_release_notes) based on [3.8](https://docs.moodle.org/dev/Moodle_3.8_release_notes), with URL _box/moodle_
- [WordPress 5.3.2+](https://wordpress.org/news/2019/12/wordpress-5-3-2-maintenance-release/) based on [5.3](https://wordpress.org/news/2019/11/kirk/), with URL _box/wordpress_
- [Kiwix 3.0.3](https://en.wikipedia.org/wiki/Kiwix) ([changelog](https://github.com/kiwix/kiwix-tools/blob/master/Changelog)) with URL _box/kiwix_
- [Minetest 5.1.1 Server](https://www.minetest.net/) ([changelog](https://dev.minetest.net/Changelog#5.1.0_.E2.86.92_5.1.1)). Allows client machines with the 5.x Minetest app to run this Minecraft-like collaborative game in a shared virtual environment.
- [Sugarizer 1.3.0](https://groups.google.com/forum/m/#!topic/unleashkids/8vgGJ_LG_CA) ([changelog](https://github.com/llaske/sugarizer/blob/master/CHANGELOG.md#130---2020-03-27)) using [Sugarizer Server 1.2.0](https://github.com/llaske/sugarizer-server/) ([changelog](https://github.com/llaske/sugarizer-server/blob/master/CHANGELOG.md#120---2019-12-01)) with URL _box/sugarizer_
- [MediaWiki 1.34.1](https://mediawiki.org/wiki/Release_notes/1.34) ([changelog](https://www.mediawiki.org/wiki/Release_notes/1.34#MediaWiki_1.34.1)) with URL _box/mediawiki_
- [Gitea 1.11.3](https://github.com/iiab/iiab/tree/master/roles/gitea#gitea-readme) ([changelog](https://github.com/go-gitea/gitea/releases)) lightweight self-hosted "GitHub" version control system, to learn to code collaboratively, with URL _box/gitea_
- [phpMyAdmin 5.0.2](https://www.phpmyadmin.net/) ([changelog](https://github.com/phpmyadmin/phpmyadmin/releases)) for remote administration of MySQL
- [Node.js 12 LTS](https://medium.com/@nodejs/introducing-node-js-12-76c41a1b3f3f) ([changelog](https://nodejs.org/en/blog/release/))  <sub><sub>[PR #2075](https://github.com/iiab/iiab/pull/2075)</sub></sub>
- [WikiHow](https://wikihow.com/) is now searchable in Spanish  <sub><sub>[PR #2198](https://github.com/iiab/iiab/pull/2198)</sub></sub>

### What might future versions bring?

- Restructuring of OSM (OpenStreetMap) <sub><sub>[#877](https://github.com/iiab/iiab/issues/877), [#1726](https://github.com/iiab/iiab/issues/1726) and [similar](https://github.com/iiab/iiab/search?q=OSM&type=Issues)</sub></sub>
- Automatic installation of "content bouquets" during IIAB installation (up to 64 GB or 128 GB typically) so new implementers can pick a language &mdash; _then hit the ground running._  <sub><sub>[#1958](https://github.com/iiab/iiab/issues/1958)</sub></sub>
- IIAB out-of-box experience on "Raspbian With Desktop" OS.  <sub><sub>[#1979](https://github.com/iiab/iiab/issues/1979)</sub></sub>  With [HOW-TO Videos](http://iiab.net/info/videos/) for enterprising teachers and students, with actionable subtitles in common languages.  <sub><sub>[#1975](https://github.com/iiab/iiab/issues/1975)</sub></sub>
- [Matomo](https://matomo.org/) for usage analytics, alongside some careful re-thinking of how IIAB teachers and content contributors can learn from users' needs.  <sub><sub>[#1762](https://github.com/iiab/iiab/issues/1762)</sub></sub>
- [Magrit 0.8.11](http://magrit.cnrs.fr/) for civic/local mapmaking, with URL _box/magrit_ ? <sub><sub>[PR #1579](https://github.com/iiab/iiab/pull/1579)</sub></sub>
- For a more detailed list, see the [Internet-in-a-Box (IIAB) 7.2 Milestone](https://github.com/iiab/iiab/milestone/7)

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's quality content collaborations across ALL communities!_

[[Many Contributors TBA](http://internet-in-a-box.org/pages/contributing.html)]

Join our Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

- On Ubuntu 18.04, IIAB's [1-line installer](http://download.iiab.io) must be run as root  <sub><sub>[#1714](https://github.com/iiab/iiab/issues/1714)</sub></sub>
- If you install IIAB on one kind of Raspberry Pi (e.g. RPi 4) and then move the microSD card to another kind of Raspberry Pi (e.g. RPi 3 / 3 B+, or e.g. RPi Zero W) you'll likely need to run `rfkill unblock wifi`.  Do this after the microSD is inserted into the new hardware, so that hostapd (and your IIAB hotspot!) work.  <sub><sub>[#2265](https://github.com/iiab/iiab/issues/2265)</sub></sub>
- Admin Console removes comments from local_vars.yml  <sub><sub>[#1964](https://github.com/iiab/iiab/issues/1964)</sub></sub>
- Nextcloud video(s) might not play?  <sub><sub>[#2262](https://github.com/iiab/iiab/issues/2262)</sub></sub>
- Kolibri blocks you from logging in at times, with its login page infinitely/rapidly looping.  Deleting your browser's cookies is not quite enough to work around this problem, but running your browser in incognito/privacy mode does work.  <sub><sub>[#1532](https://github.com/iiab/iiab/issues/1532)</sub></sub>
- Sugarizer generally requires MongoDB, which is no longer packaged by Linux OS's like Debian 10 Buster.  <sub><sub>[#1437](https://github.com/iiab/iiab/issues/1437)</sub></sub>
- Node.js applications like Asterisk/FreePBX, Node-RED and Sugarizer won't work on Raspberry Pi Zero W (ARMv6) if you installed Node.js while on RPi 3, 3 B+ (ARMv7) or RPi 4 (ARMv8).  If necessary, run `apt remove nodejs` then ([attempt!](https://nodered.org/docs/hardware/raspberrypi#swapping-sd-cards)) things like `cd /opt/iiab/iiab; ./runrole nodejs` to [install Node.js](https://github.com/iiab/iiab/blob/master/roles/nodejs/tasks/main.yml) _on the Raspberry Pi Zero W itself_ — before proceeding to install Asterisk/FreePBX, Node-RED and/or Sugarizer.  <sub><sub>[#2082](https://github.com/iiab/iiab/issues/2082)</sub></sub>
- A few residual issues remain at: https://github.com/iiab/iiab/milestone/6