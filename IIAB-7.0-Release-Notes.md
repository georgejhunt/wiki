### _DRAFT_

[Internet-in-a-Box (IIAB)](http://internet-in-a-box.org) version 7.0 will build upon [IIAB 6.7](https://github.com/iiab/iiab/wiki/IIAB-6.7-Release-Notes), to be released Q2 2019 ([Roadmap Ideas](https://github.com/iiab/iiab/wiki/IIAB-6.7-Release-Notes#what-might-future-versions-bring), [GitHub Milestone](https://github.com/iiab/iiab/milestone/5), [Wiki](http://wiki.laptop.org/go/IIAB/7.0)) in service of DIY digital libraries for schools, clinics and communities across all corners of the planet.

See our Frequently Asked Questions ([FAQ.IIAB.IO](http://wiki.laptop.org/go/IIAB/FAQ)) and consider installing a pre-release today:

<p align="center">
  <b><a href=http://download.iiab.io>download.iiab.io</a></b>
  <!--[download.iiab.io](http://download.iiab.io)-->
</p>

Please [join us in making this major release happen](http://internet-in-a-box.org/pages/contributing.html), Thank You!

### About

Internet-in-a-Box brings the [Internet's crown jewels](http://internet-in-a-box.org/#quality-content) and the very best of the World’s Free Knowledge (Wikipedia, Khan Academy, OpenStreetMap, E-Books, etc) to those who are burning for learning — but just happen to be offline.

Use <b>drag-and-drop</b> to customize this "learning hotspot" with local gems too — tailored to the needs of your school, your library, your prison, your region and/or your very own family!

Why not build your own [LIBRARY OF ALEXANDRIA](https://www.youtube.com/channel/UC0cBGCxr_WPBPa3IqPVEe3g) with a $35 Raspberry Pi computer, starting today?

### What's New?

* [OpenStreetMap](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_add_zoomable_maps_for_my_region.3F) is like Google Maps but better, for schools especially, as it works offline and avoids all the advertising.  Implementers can easily download detailed vector-based Map Packs for an entire continent, or the entire world!  Please try it out (http://box.lan/admin > Install Content > Get Map Region) and don't hesitate to [ask us](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_best_places_for_community_support.3F) about satellite imagery options coming soon!  _Documentation is still coming together as of 2019-06-14, thank you for testing & providing feedback!_  <sub><sub>[#1710](https://github.com/iiab/iiab/issues/1710)</sub></sub>
* Beautify your IIAB home page (http://box) with new click-to-install logos for each of your Content Packs & IIAB Apps.  Rewrite any of their descriptions in your own language, also from IIAB's Admin Console (http://box.lan/admin) so students know exactly what's available to them, in their own language!  <sub><sub>[#1708](https://github.com/iiab/iiab/issues/1708)</sub></sub>
* [Internet Archive Decentralized Web](https://dweb.archive.org/) helps you create your own offline digital library.  It includes a crawler that can regularly synchronize local collections, against a list of Internet Archive items and collections, and those collections can be moved between installations.  When connected to the internet, it works as a Proxy, i.e. it will store Internet Archive content the user views for later offline viewing.  With URL _box:4244 (box/archive in future)_  <sub><sub>[PR #1617](https://github.com/iiab/iiab/pull/1617)</sub></sub>
* [Gitea 1.8.2](https://github.com/iiab/iiab/tree/master/roles/gitea#gitea-readme) ([changelog](https://github.com/go-gitea/gitea/releases)) lightweight self-hosted "GitHub", with URL _box/gitea_  <sub><sub>[PR #1242](https://github.com/iiab/iiab/pull/1242)</sub></sub>
* Please see ["What might future versions bring?"](#what-might-future-versions-bring)

### What's Upgraded?

* Internet-in-a-Box installation (http://download.iiab.io) is much more self-explanatory, hiding the details of [Ansible 2.8](https://docs.ansible.com/ansible/devel/porting_guides/porting_guide_2.8.html) so implementers can focus on [content curation](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_customize_my_Internet-in-a-Box_home_page.3F) instead!  <sub><sub>[#1028](https://github.com/iiab/iiab/issues/1028)</sub></sub>
  * Fix your Internet-in-a-Box's date and time automatically, when a nearby smartphone visits your IIAB home page (http://box).  <sub><sub>[#1680](https://github.com/iiab/iiab/issues/1680)</sub></sub>
  * Your IIAB's firewall (iptables) and remote connections (OpenVPN) are much easier to set up.  <sub><sub>[PR #1654](https://github.com/iiab/iiab/pull/1654)</sub></sub> <sub><sub>[PR #1677](https://github.com/iiab/iiab/pull/1677)</sub></sub>
* [Kolibri 0.12.3](https://github.com/iiab/iiab/tree/master/roles/kolibri) (<!--[Announcement](https://medium.com/kolibri-releases), -->[Release Notes](https://github.com/learningequality/kolibri/blob/v0.12.0/CHANGELOG.rst#0120), [Changelog](https://github.com/learningequality/kolibri/releases), [User Guide](https://kolibri.readthedocs.io/)) with new Physics/Chemistry LibreTexts, and URL _box/kolibri_  <sub><sub>[#1545](https://github.com/iiab/iiab/issues/1545)</sub></sub> <sub><sub>[#1608](https://github.com/iiab/iiab/issues/1608)</sub></sub>
* [Nextcloud 15.0.8+](https://nextcloud.com/changelog/#latest15) or [Nextcloud 16.0.1+](https://nextcloud.com/changelog/#latest16) if your GNU/Linux OS is recent enough to support PHP 7.1+, with 15.0.9 and 16.0.2 expected 2019-06-27 ([blog](https://nextcloud.com/blog/)) with URL _box/nextcloud_  <sub><sub>[PR #1667](https://github.com/iiab/iiab/pull/1667)</sub></sub> <sub><sub>[#1734](https://github.com/iiab/iiab/issues/1734)</sub></sub>
* [Lokole 0.4.2](https://github.com/iiab/iiab/tree/master/roles/lokole#lokole-readme) ([changelog](https://github.com/ascoderu/opwen-webapp/releases)) email for rural communities, students and teachers, with URL _box/lokole_
* [Moodle 3.5.6 LTS](https://docs.moodle.org/dev/Moodle_3.5.6_release_notes) building on [3.5 LTS](https://docs.moodle.org/dev/Releases#Moodle_3.5_.28LTS.29), with URL _box/moodle_  <sub><sub>[#1529](https://github.com/iiab/iiab/issues/1529)</sub></sub>
* [WordPress 5.2.1](https://wordpress.org/news/2019/05/wordpress-5-2-1-maintenance-release/) -> [5.2.2 ETA 2019-06-18](https://make.wordpress.org/core/), based on [5.2](https://wordpress.org/news/2019/05/jaco/) with URL _box/wordpress_  <sub><sub>[#1703](https://github.com/iiab/iiab/issues/1703)</sub></sub>
* [Kiwix 2.0.0](https://github.com/kiwix/kiwix-tools/blob/master/Changelog) ([changelog](https://github.com/kiwix/kiwix-tools/blob/master/Changelog)) with URL _box/kiwix_  <sub><sub>[PR #1706](https://github.com/iiab/iiab/pull/1706)</sub></sub>
* [Calibre-Web 0.6.3](https://github.com/janeczku/calibre-web#about) ([changelog](https://github.com/janeczku/calibre-web/releases)) now does a better job showing visual thumbnail previews e.g. for locally uploaded PDF's, with URL _box/books_  <sub><sub>[PR #1565](https://github.com/iiab/iiab/pull/1565)</sub></sub> <sub><sub>[#1624](https://github.com/iiab/iiab/issues/1624)</sub></sub>
* [Calibre 3.44](https://calibre-ebook.com/whats-new) on x86_64 and 3.39.1 on Raspberry Pi, with URL _box:8080_
* [Sugarizer Server 1.1.0](https://github.com/llaske/sugarizer-server/) ([changelog](https://github.com/llaske/sugarizer-server/blob/master/CHANGELOG.md)) with URL _box/sugarizer_  <sub><sub>[PR #1657](https://github.com/iiab/iiab/pull/1657)</sub></sub>
* [MediaWiki 1.32.1](https://mediawiki.org/wiki/Release_notes/1.32) with URL _box/mediawiki_
* [Elgg 2.3.13 LTS](https://github.com/Elgg/Elgg/blob/2.3.13/CHANGELOG.md) with URL _box/elgg_  <sub><sub>[PR #1730](https://github.com/iiab/iiab/pull/1730)</sub></sub>

### What might future versions bring?

* New commands like `iiab-diagnostics` can speed up remote support by 10X in many situations, ETA June 2019.  <sub><sub>[#1575](https://github.com/iiab/iiab/issues/1575)</sub></sub> <sub><sub>[PR #1596](https://github.com/iiab/iiab/pull/1596)</sub></sub>
* Bluetooth access to IIAB's Admin Console, for IIAB field operators/administrators and advanced teachers!  <sub><sub>[PR #1716](https://github.com/iiab/iiab/pull/1716)</sub></sub>
* [Magrit 0.8.11](http://magrit.cnrs.fr/) for civic/local mapmaking, with URL _box/magrit_ ? <sub><sub>[PR #1579](https://github.com/iiab/iiab/pull/1579)</sub></sub>

### Known Issues

* IIAB's home page (http://box) will not display in browsers like Windows 7's Internet Explorer 11.  Please install a modern browser e.g. Firefox or Chrome ([js-menu](https://github.com/iiab/iiab-admin-console/tree/master/roles/js-menu) requires a more recent version of JavaScript).  <sub><sub>[#1517](https://github.com/iiab/iiab/issues/1517)</sub></sub>
* Sugarizer requires MongoDB which is no longer packaged by Linux OS's like Debian 10 Buster, due to licensing issues.  <sub><sub>[PR #1437](https://github.com/iiab/iiab/issues/1437)</sub></sub>
* Node.js applications like Asterisk/FreePBX, Node-RED and Sugarizer [won't work](https://nodered.org/docs/hardware/raspberrypi#swapping-sd-cards) on Raspberry Pi Zero W (ARM6) *if* you installed Node.js while on RPi 3 or 3 B+ (ARM7).  If necessary, run `apt remove nodejs` then `cd /opt/iiab/iiab` then (attempt!) [./runrole nodejs](https://github.com/iiab/iiab/blob/master/roles/nodejs/tasks/main.yml) _on the Raspberry Pi Zero W itself_ — before proceeding to install Asterisk/FreePBX, Node-RED and/or Sugarizer.