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

* [Gitea 1.8.0](https://github.com/iiab/iiab/tree/master/roles/gitea#gitea-readme) lightweight self-hosted "GitHub", with URL _box/gitea_  <sub><sub>[PR #1242](https://github.com/iiab/iiab/pull/1242)</sub></sub>
* [OpenStreetMap](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_add_zoomable_maps_for_my_region.3F) is like Google Maps but better, for schools especially, as it works offline and avoids all the advertising.  Implementers can easily download detailed "vector maps" for an entire continent, or the entire world!  _CAUTION: the Admin Console to download and auto-install continents is not yet polished as of 2019-04-22._  Also: [ask us](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_best_places_for_community_support.3F) about satellite imagery expected later in 2019.  <sub><sub>[#877](https://github.com/iiab/iiab/issues/877)</sub></sub>
* [Magrit 0.8.11](http://magrit.cnrs.fr/) for civic/local mapmaking (ETA May 2019?) with URL _box/magrit_ ? <sub><sub>[PR #1579](https://github.com/iiab/iiab/pull/1579)</sub></sub>
* [Internet Archive Decentralized Web](https://dweb.archive.org/) integration (ETA May 2019?)  with URL _box:4244_ ?  <sub><sub>[PR #1617](https://github.com/iiab/iiab/pull/1617)</sub></sub>
* Please see ["What might future versions bring?"](https://github.com/iiab/iiab/wiki/IIAB-6.7-Release-Notes#what-might-future-versions-bring)

### What's Upgraded?

* Internet-in-a-Box installation (http://d.iiab.io) is much more self-explanatory!  <sub><sub>[#1583](https://github.com/iiab/iiab/issues/1583)</sub></sub>
* [Kolibri 0.12.2](https://github.com/iiab/iiab/tree/master/roles/kolibri) (<!--[Announcement](https://medium.com/kolibri-releases), -->[Release Notes](https://github.com/learningequality/kolibri/blob/v0.12.0/CHANGELOG.rst#0120), [Changelog](https://github.com/learningequality/kolibri/releases), [User Guide](https://kolibri.readthedocs.io/)) with new Physics/Chemistry LibreTexts, and URL _box/kolibri_  <sub><sub>[#1545](https://github.com/iiab/iiab/issues/1545)</sub></sub>
* [Nextcloud 15](https://nextcloud.com/changelog/#latest15) ([blog](https://nextcloud.com/blog/)) with URL _box/nextcloud_  <sub><sub>[#1614](https://github.com/iiab/iiab/pull/1614)</sub></sub>
* [Lokole 0.1.39](https://github.com/iiab/iiab/tree/master/roles/lokole#lokole-readme) email for rural communities, students and teachers, with URL _box/lokole_
* [Moodle 3.5.5 LTS](https://docs.moodle.org/dev/Moodle_3.5.5_release_notes) building on [3.5 LTS](https://docs.moodle.org/dev/Releases#Moodle_3.5_.28LTS.29), with URL _box/moodle_  <sub><sub>[#1528](https://github.com/iiab/iiab/issues/1528)</sub></sub>
* [WordPress 5.1.1](https://wordpress.org/news/)  with URL _box/wordpress_  <sub><sub>[PR #1535](https://github.com/iiab/iiab/pull/1535)</sub></sub>
* [Kiwix 1.2.0](https://github.com/kiwix/kiwix-tools/blob/master/Changelog) with URL _box/kiwix_  <sub><sub>[PR #1598](https://github.com/iiab/iiab/pull/1598)</sub></sub>
* [Calibre-Web](https://github.com/janeczku/calibre-web) now does a better job showing visual thumbnail previews e.g. for locally uploaded PDF's  <sub><sub>[PR #1565](https://github.com/iiab/iiab/pull/1565)</sub></sub>
* [Calibre 3.42](https://calibre-ebook.com/whats-new) on x86_64 and 3.39.1 on Raspberry Pi, with URL _box:8080_
* [Elgg 2.3.12 LTS](https://github.com/Elgg/Elgg/blob/2.3.11/CHANGELOG.md) with URL _box/elgg_  <sub><sub>[PR #1607](https://github.com/iiab/iiab/pull/1607)</sub></sub>

### Known Issues

* Sugarizer requires MongoDB which is no longer packaged by Linux OS's like Debian 10 Buster, due to licensing issues.  <sub><sub>[PR #1437](https://github.com/iiab/iiab/issues/1437)</sub></sub>