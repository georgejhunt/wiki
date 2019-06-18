# Internet-in-a-Box (IIAB) Maps

[Internet-in-a-Box](http://Internet-in-a-Box.org) (IIAB) provides offline Map Packs that are like Google Maps but better, for schools especially, as they work offline and avoid all the advertising.

These Map Packs are compressed and use vector (not bitmap) techniques so you can easily download and install an entire continent/region, or the entire world, also including satellite photos:

- Zoomable, detailed maps (14 levels of vector zoom, scales beautifully to 18 levels of zoom)
- Every IIAB Map Pack now includes satellite photos (10 levels of zoom) from [Sentinel](https://s2maps.eu/)
- [OpenStreetMap](https://www.openstreetmap.org/) content updates approximately annually, thanks to [OpenMapTiles.org](https://OpenMapTiles.org)
- Self-contained IIAB Map Packs (about 4-to-23 GB each) are now packaged up and available for:
  - Major Continents
  - The Middle East
  - Central America & the Caribbean
  - The Entire World &mdash; which now fits within ~53 GB ([Live Demo!](http://iiab.me/maps))

This represents the state-of-the-art as of June 2019, for IIAB 7.0.  For nuts & bolts details as to how this came together, please see [Credits](#credits), [Software (Source Code)](#software-source-code) and [Links & Advanced Topics](#links--advanced-topics) sections below.

## How do I install an IIAB Map Pack for my region?

1. If you have not yet, install [Internet-in-a-Box](http://internet-in-a-box.org) (IIAB) [7.0](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes) (or higher) from http://download.iiab.io

2. Use its Admin Console (http://box.lan/admin, default passwords at http://FAQ.IIAB.IO) to click `Install Content` (on top) > `Get Map Region` (on the left).

3. Pick a checkbox on the left to download, unpack and install the Map Region (Map Pack) you want.  As you hover (mouse over) the choices on the left, colorful bounding boxes light up on the world map on the right &mdash; to help you choose the Map Pack most suitable for your region:

   - As of June 2019 you can choose among each of the major continents, Central America (3.77 GB), the Middle East (7.66 GB) or the World (53.17 GB).

4. After making your choice, kick off your Map Pack download/installation using the `Install Selected Region` button:

   - Please be patient as this can sometimes take a few hours, depending on your Internet connection etc!  You can monitor the progress by clicking `Utilities` (on top) > `Display Job Status` (on the left).

   - Here's a working example of IIAB maps in action, so you know how they'll appear after your chosen Map Pack unpacks and installs itself, including fully-zoomable details of all continents in this example: http://iiab.me/maps

5. Once your Map Pack is installed, try it out at http://box/maps &mdash; and also look over your new IIAB home page (typically http://box, or http://172.18.96.1, or http://box.local) where a new Content Pack should appear, briefly describing the Map Pack you installed &mdash; for students and teachers to click on!

## How do I upgrade an IIAB Map Pack?

In the weeks/months after installing your IIAB Map Pack, you might notice that a new Map Pack is published, e.g. if you monitor these "map catalog" links showing the latest available:

- https://archive.org/search.php?query=osm-vector&sort=-publicdate
- http://download.iiab.io/content/OSM/vector-tiles/maplist/assets/regions.json
- https://github.com/georgejhunt/maps/blob/new-bboxes/resources/regions.json _(out of date?)_
- https://github.com/iiab/maps/blob/master/osm-source/ukids/assets/regions.json _(out of date?)_

Just for now (as of June 2019, for [IIAB 7.0](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes)) the process of upgrading an IIAB Map Pack needs to be done manually:

1. Back up your Internet-in-a-Box (IIAB) using one of the techniques described in http://FAQ.IIAB.IO > "How do I back up, shrink & copy IIAB microSD cards?"

2. Delete your existing/installed Map Pack from within `/library/www/osm-vector-maps` &mdash; this will be a sub-directory named something like `en-osm-omt_africa_2017-07-03_v0.2` &mdash; that contains many gigabytes.

3. Use a text editor like `nano` to remove the deleted Map Pack's stanza (all 8 lines of it) from:

    `/library/www/html/common/assets/vector-map-idx.json`

4. Run this 7-line recipe at the Linux command-line, to upgrade all your IIAB software:

    ```
    sudo su -

    cd /opt/iiab/iiab
    git pull
    ./iiab-install --reinstall    # takes about 20+ min (or run "./runrole osm-vector-maps" which is faster)

    cd /opt/iiab/iiab-admin-console
    git pull
    ./install                     # takes about 3-5 min
    ```

5. Get your **new** Map Pack by following the original instructions above ("How do I install an IIAB Map Pack for my region?") i.e. http://box.lan/admin > Install Content > Get Map Region.

6. Beautify, update or [customize your IIAB home page](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_customize_my_Internet-in-a-Box_home_page.3F) (e.g. http://box) as necessary!

## What might future IIAB Maps bring?

_INVITATION: If you can help ongoing efforts to polish maps for children in offline schools in all countries, directly contributing to [beautifying OpenStreetMap (VIDEO)](https://youtu.be/HJub6U_U7Mg) thereby bringing Earth to life for all, Thank You!  Read more at ([#877](https://github.com/iiab/iiab/issues/877#issuecomment-405935272)) and please do [get in touch](http://FAQ.IIAB.IO/#What_are_the_best_places_for_community_support.3F) to learn more!_

_Thanks for your help evolving this into a continuously more friendly community product, as Usability Engineering begins right here &mdash; thanks to all who can assist!  Background: Internet-in-a-Box is a [volunteer community](http://internet-in-a-box.org/pages/contributing.html) that greatly welcomes your suggestions and contributions !_

- Map issues currently being discussed or worked on: https://github.com/iiab/iiab/issues?q=is%3Aopen+OSM
- Individual .mbtiles Map Packs (e.g. smaller map regions, for cities, countries, etc) might in future be directly downloadable to your IIAB, as new ones are published here: https://openmaptiles.com/downloads/planet/
- Multiple Map Packs might be downloadable to your IIAB, all of them viewable thru the same http://box/maps URL, possibly by combining their .mbtiles files into a single unified .mbtiles file, e.g. using [append2region](https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/append2region).
- Descriptions of Map Packs (on your http://box IIAB Home Page) could offer more tips & tricks for teachers and students, e.g. how to search for cities etc.
- http://box/maps/maplist/ might show more of a visual catalog of what maps were available around the time your IIAB was originally installed, or most recently updated?
- Please [suggest](http://FAQ.IIAB.IO/#What_are_the_best_places_for_community_support.3F) the highest priority mapmaking needs and/or how you might help!

## Credits

Much of the original work on IIAB Maps was coordinated by Braddock Gaskill and Joel Steres in 2012-2015.

More recently George Hunt refined city search, moved to vector-based Map Packs, and added satellite photos &mdash; leading to major advances in Sept 2018 ([IIAB 6.6](https://github.com/iiab/iiab/wiki/IIAB-6.6-Release-Notes)) and June 2019 ([IIAB 7.0](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes)).

Thank you also to Tim Moody, Adam Holt, Anish Mangal, Avni Khatri, Mir Rodríguez Lombardo, Minh Nguyen, Paul Norman, Jérôme Gagnon-Voyer, Nick Doiron & other volunteer professionals from the [OpenStreetMap community](https://www.openstreetmap.org/) who are making this tremendous, ongoing progress possible!

## Software (Source Code)

- https://github.com/iiab/maps
- https://github.com/iiab/iiab/tree/master/roles/osm-vector-maps

## Links & Advanced Topics

In reverse chronological order:

- [FAQ.IIAB.IO](http://FAQ.IIAB.IO) > ["How do I add zoomable maps for my region?"](http://FAQ.IIAB.IO#How_do_I_add_zoomable_maps_for_my_region.3F)
- Living Docs for IIAB 7.0 Maps, June 2019: https://github.com/iiab/iiab/issues/1710
- History And Architecture, June 2019: https://github.com/iiab/maps/blob/master/docs/README.md#history-and-architecture
- "Make your own IIAB Map Pack" draft notes, May 2019: https://github.com/georgejhunt/maps/blob/simple/generate-regions/readme.md
- IIAB 6.6 Guide, Sept 2018: https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/README.md
- George Hunt Design Doc 2, July 2018: https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/Design-Decisions.md
- "Package up vector-based OSM maps" task list, July 2018 onwards: https://github.com/iiab/iiab/issues/877#issuecomment-405935272
- George Hunt Design Doc 1, April 2018: https://github.com/georgejhunt/iiab-factory/blob/vector-maps/content/vector-tiles/Design-Decisions.md
- Jérôme Gagnon-Voyer 2015 Design Doc 2, August 2015: https://jeromegagnonvoyer.wordpress.com/2015/08/21/offline-solution-for-openstreetmap-osm/
- Jérôme Gagnon-Voyer 2015 Design Doc 1, August 2015: https://jeromegagnonvoyer.wordpress.com/2015/08/06/merging-multiple-mbtiles-together/