### _DRAFT_

[Internet-in-a-Box (IIAB)](http://internet-in-a-box.org) version 7.0 will build upon [IIAB 6.7](https://github.com/iiab/iiab/wiki/IIAB-6.7-Release-Notes), to be released mid-2019 ([Roadmap Ideas](https://github.com/iiab/iiab/wiki/IIAB-6.7-Release-Notes#what-might-future-versions-bring), [GitHub Milestone](https://github.com/iiab/iiab/milestone/5), [Wiki](http://wiki.laptop.org/go/IIAB/7.0)) in service of DIY digital libraries for schools, clinics and communities across all corners of the planet.

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

* [Raspberry Pi 4](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/) and [Raspbian Buster](https://raspberrypi.org/downloads/raspbian/) support, _allowing IIAB installs that are 3X faster!_  IIAB also now supports the brand new [Debian 10 "Buster"](https://wiki.debian.org/DebianBuster) OS, on regular PC's and laptops.
* [OpenStreetMap](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_add_zoomable_maps_for_my_region.3F) is like Google Maps but better, for schools especially, as it works offline and avoids all the advertising.  Implementers can easily download detailed vector-based Map Packs for an entire continent, or the entire world!  Please try it out (after you install IIAB, go to its **http://box.lan/admin > Install Content > Get Map Region**) and to [ask us](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_best_places_for_community_support.3F) about satellite imagery and other mapmaking / map-mixing options _[coming soon.](https://github.com/iiab/iiab/wiki/IIAB-Maps)_  With URL _box/maps_  <sub><sub>[#1710](https://github.com/iiab/iiab/issues/1710)</sub></sub>
* [Internet Archive Decentralized Web](https://github.com/iiab/iiab/tree/master/roles/internetarchive#internet-archive-universal-library--decentralized-web-readme) helps you create your own offline digital library.  It includes a crawler that can regularly synchronize local collections, against a list of Internet Archive items and collections, and those collections can be moved between installations.  When connected to the internet, it works as a Proxy, i.e. it will store Internet Archive content the user views for later offline viewing.  With URL _box:4244 (box/archive in future)_  <sub><sub>[PR #1617](https://github.com/iiab/iiab/pull/1617)</sub></sub>
* Beautify your IIAB home page (http://box) with new click-to-install logos for each of your Content Packs & IIAB Apps.  Rewrite any of their descriptions in your own language, also from IIAB's Admin Console (**http://box.lan/admin > Content Menus**) so students know exactly what's available to them, in their own language!  <sub><sub>[#1708](https://github.com/iiab/iiab/issues/1708)</sub></sub>
* [Gitea 1.8.3](https://github.com/iiab/iiab/tree/master/roles/gitea#gitea-readme) ([changelog](https://github.com/go-gitea/gitea/releases)) lightweight self-hosted "GitHub" version control system, to learn to code collaboratively, with URL _box/gitea_  <sub><sub>[PR #1242](https://github.com/iiab/iiab/pull/1242)</sub></sub>
* [AzuraCast 0.9.5.1](https://github.com/iiab/iiab/tree/master/roles/azuracast#azuracast-readme) is a self-hosted, all-in-one radio station platform.  Use AzuraCast to schedule podcasts, music, and even do live streaming of audio content.  A variety of streaming formats are supported.  <sub><sub>[PR #1733](https://github.com/iiab/iiab/pull/1733)</sub></sub>
* Nearby smartphones and laptops/devices can update your IIAB's date and time automatically, simply by browsing to your IIAB home page (http://box).  This can be a lifesaver in offline environments, with low-end Raspberry Pi servers that contain no RTC (i.e. real-time clock and coin cell battery).  So they don't completely lose track of the current day and time.  <sub><sub>[#1680](https://github.com/iiab/iiab/issues/1680)</sub></sub>
* [Bluetooth](https://github.com/iiab/iiab/tree/master/roles/bluetooth) access to IIAB's Admin Console, for IIAB field operators/administrators and advanced teachers too!  <sub><sub>[PR #1716](https://github.com/iiab/iiab/pull/1716)</sub></sub> <sub><sub>[PR iiab/iiab-admin-console#209](https://github.com/iiab/iiab-admin-console/pull/209)</sub></sub>
* [iiab-diagnostics](https://github.com/iiab/iiab/blob/master/scripts/iiab-diagnostics.README.md) dramatically speeds up remote troubleshooting and community support, so that Internet-in-a-Box Field Teams and Dev Teams can communicate efficiently (while each focusing on what they do best!)  <sub><sub>[#1575](https://github.com/iiab/iiab/issues/1575)</sub></sub> <sub><sub>[PR #1763](https://github.com/iiab/iiab/pull/1763)</sub></sub>
* Please see ["What might future versions bring?"](#what-might-future-versions-bring)

### What's Upgraded?

* Internet-in-a-Box installation (http://download.iiab.io) is much more self-explanatory, hiding the details of [Ansible 2.8](https://docs.ansible.com/ansible/devel/porting_guides/porting_guide_2.8.html) so implementers can focus on [content curation](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_customize_my_Internet-in-a-Box_home_page.3F) instead!  <sub><sub>[#1028](https://github.com/iiab/iiab/issues/1028)</sub></sub>
  * Your IIAB's firewall (iptables) and remote connections (OpenVPN) are now much easier to set up.  <sub><sub>[PR #1654](https://github.com/iiab/iiab/pull/1654)</sub></sub> <sub><sub>[PR #1677](https://github.com/iiab/iiab/pull/1677)</sub></sub>
  * OpenVPN was made substantially more reliable &mdash; it now works even when DNS does not.  <sub><sub>[PR #1752](https://github.com/iiab/iiab/pull/1752)</sub></sub> 
* [Kolibri 0.12.5+ or 0.12.6+](https://github.com/iiab/iiab/tree/master/roles/kolibri) (<!--[Announcement](https://medium.com/kolibri-releases), -->[changelog](https://github.com/learningequality/kolibri/blob/develop/CHANGELOG.md), [user guide](https://kolibri.readthedocs.io/)) with new Physics/Chemistry LibreTexts, and URL _box/kolibri_  <sub><sub>[#1545](https://github.com/iiab/iiab/issues/1545)</sub></sub> <sub><sub>[#1736](https://github.com/iiab/iiab/issues/1736)</sub></sub>
* [Nextcloud 16.0.2+](https://nextcloud.com/changelog/#latest16) ([blog](https://nextcloud.com/blog/)) with URL _box/nextcloud_  <sub><sub>[#1734](https://github.com/iiab/iiab/issues/1734)</sub></sub>
* [Lokole 0.4.4](https://github.com/iiab/iiab/tree/master/roles/lokole#lokole-readme) ([changelog](https://github.com/ascoderu/opwen-webapp/releases)) email for rural communities, students and teachers, with URL _box/lokole_  <sub><sub>[PR #1853](https://github.com/iiab/iiab/pull/1853)</sub></sub>
* [Moodle 3.7.1+ LTS](https://docs.moodle.org/dev/Moodle_3.7.1_release_notes), with URL _box/moodle_  <sub><sub>[#1658](https://github.com/iiab/iiab/issues/1658)</sub></sub>
* [WordPress 5.2.2+](https://wordpress.org/news/2019/06/wordpress-5-2-2-maintenance-release/) based on [5.2](https://wordpress.org/news/2019/05/jaco/), with URL _box/wordpress_  <sub><sub>[#1703](https://github.com/iiab/iiab/issues/1703)</sub></sub>
* [Kiwix 2.0.0](https://github.com/kiwix/kiwix-tools/blob/master/Changelog) ([changelog](https://github.com/kiwix/kiwix-tools/blob/master/Changelog)) with URL _box/kiwix_  <sub><sub>[PR #1706](https://github.com/iiab/iiab/pull/1706)</sub></sub>
* [Calibre-Web 0.6.3](https://github.com/janeczku/calibre-web#about) ([changelog](https://github.com/janeczku/calibre-web/releases)) now does a better job showing visual thumbnail previews e.g. for locally uploaded PDF's, with URL _box/books_  <sub><sub>[PR #1565](https://github.com/iiab/iiab/pull/1565)</sub></sub> <sub><sub>[#1624](https://github.com/iiab/iiab/issues/1624)</sub></sub>
* [Calibre 3.44+](https://calibre-ebook.com/whats-new) on x86_64 and 3.39.1 on Raspberry Pi, with URL _box:8080_
* [Sugarizer Server 1.1.1](https://github.com/llaske/sugarizer-server/) ([changelog](https://github.com/llaske/sugarizer-server/blob/master/CHANGELOG.md)) with URL _box/sugarizer_  <sub><sub>[PR #1657](https://github.com/iiab/iiab/pull/1657)</sub></sub>
* [MediaWiki 1.33.0](https://mediawiki.org/wiki/Release_notes/1.33) with URL _box/mediawiki_  <sub><sub>[PR #1809](https://github.com/iiab/iiab/pull/1809)</sub></sub>
* [Elgg 2.3.13 LTS](https://github.com/Elgg/Elgg/blob/2.3.13/CHANGELOG.md) with URL _box/elgg_  <sub><sub>[PR #1730](https://github.com/iiab/iiab/pull/1730)</sub></sub>

### What might future versions bring?

* Instant submission of Content Pack descriptions/logos for your IIAB home page, so that non-technical implementers/educators around the planet can rapidly & efficiently share ["menu item definitions"](https://github.com/iiab/iiab/wiki/IIAB-Menuing) &mdash; _putting community action into high gear._  <sub><sub>[#1831](https://github.com/iiab/iiab/issues/1831)</sub></sub>
* [Matomo](https://matomo.org/) for usage analytics, alongside some careful re-thinking of how IIAB teachers and content contributors can learn from users' needs.  <sub><sub>[#1762](https://github.com/iiab/iiab/issues/1762)</sub></sub>
* [Magrit 0.8.11](http://magrit.cnrs.fr/) for civic/local mapmaking, with URL _box/magrit_ ? <sub><sub>[PR #1579](https://github.com/iiab/iiab/pull/1579)</sub></sub>
* [Cham](https://github.com/eka-foundation/cham) is a lightweight live video streaming platform with adaptive bitrates for IIAB.  <sub><sub>[PR #1743](https://github.com/iiab/iiab/pull/1743)</sub></sub>
* For a more detailed list, see the [Internet-in-a-Box (IIAB) 7.1 Milestone](https://github.com/iiab/iiab/milestone/6)

### Credits

Thank you e-v-e-r-y-o-n-e for building your own DIY Library of Alexandria.  To serve One & All.

Building on this software and designs contributed by Mir Rodríguez Lombardo, Mitra Ardron, Kurt Maier, T.K. Kang, Eric Nitschke, César López-Natarén, Joshua Kanani, Josh Dennis, Arky R., Matt Johnson, James Heilman, Sam Zidovetzki, Reno McKenzie, Anish Mangal, Avni Khatri, Blondel Mondésir, George Hunt, Tim Moody, Jerry Vonau, Adam Holt &mdash; among many others!

_Not just in your own community &mdash; but by keeping in touch with our global volunteer community network ([http://OFF.NETWORK](http://OFF.NETWORK)) each of you are providing the lifeblood "fieldback" &mdash; that keeps us motivated enabling Internet-in-a-Box's quality content collaborations across ALL communities!_

Join our Thursday calls if you too can help: [MINUTES.IIAB.IO](http://MINUTES.IIAB.IO)

Frequently Asked Questions: [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### Known Issues

* The "Mobile/Desktop" button that used to allow developing world teachers to rapidly see Content Pack details (on their own Android phones) is not working at this time.  <sub><sub>[#1775](https://github.com/iiab/iiab/issues/1775)</sub></sub>
* IIAB's home page (http://box) will not display in browsers like Windows 7's Internet Explorer 11.  Please install a modern browser e.g. Firefox or Chrome ([js-menu](https://github.com/iiab/iiab-admin-console/tree/master/roles/js-menu) requires a more recent version of JavaScript).  <sub><sub>[#1517](https://github.com/iiab/iiab/issues/1517)</sub></sub>
* Kolibri blocks you from logging in at times, with its login page infinitely/rapidly looping.  Deleting your browser's cookies is not quite enough to work around this problem, but running your browser in incognito/privacy mode does work.  <sub><sub>[#1532](https://github.com/iiab/iiab/issues/1532)</sub></sub>
  * Sometimes Kolibri does not start after reboot, if you've downloaded Kolibri Channels  <sub><sub>[#1648](https://github.com/iiab/iiab/issues/1648)</sub></sub>
* Sugarizer requires MongoDB which is no longer packaged by Linux OS's like Debian 10 Buster, due to licensing issues.  <sub><sub>[PR #1437](https://github.com/iiab/iiab/issues/1437)</sub></sub>
* Node.js applications like Asterisk/FreePBX, Node-RED and Sugarizer generally won't work on Raspberry Pi Zero W (ARMv6) *if* you installed Node.js while on RPi 3 or 3 B+ (ARMv7) or RPi 4 (ARMv8).  If necessary, run `apt remove nodejs` then ([attempt!](https://nodered.org/docs/hardware/raspberrypi#swapping-sd-cards)) things like `cd /opt/iiab/iiab; ./runrole nodejs` to [install Node.js](https://github.com/iiab/iiab/blob/master/roles/nodejs/tasks/main.yml) _on the Raspberry Pi Zero W itself_ — before proceeding to install Asterisk/FreePBX, Node-RED and/or Sugarizer.