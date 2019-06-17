# Internet-in-a-Box (IIAB) Maps

## _DRAFT_

[Internet-in-a-Box](http://Internet-in-a-Box.org) (IIAB) provides offline Map Packs that are like Google Maps but better, for schools especially, as they work offline and avoid all the advertising.

These Map Packs are compressed and use vector (not bitmap) techniques so you can easily download and install an entire continent/region, or the entire world, also including satellite photos as of June 2019:

- Zoomable, detailed maps (14 levels of vector zoom, scales beautifully to 18 levels of zoom)
- Every IIAB Map Pack now includes satellite photos (10 levels of zoom) from [Sentinel](https://s2maps.eu/)
- OpenStreetMap content updates approximately annually, thanks to [OpenMapTiles.org](https://OpenMapTiles.org)
- Self-contained IIAB Map Packs (about 4-to-23 GB each) are now packaged up and available for:
  - Major Continents
  - The Middle East
  - Central America & the Caribbean
  - The Entire World (which now fits within ~53 GB!)

Live Demo: http://iiab.me/maps

## How do I install an IIAB Map Pack for my region?

1. If you have not yet, install [Internet-in-a-Box](http://internet-in-a-box.org) (IIAB) [7.0](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes) (or higher) from http://download.iiab.io

2. Use its Admin Console (http://box.lan/admin, default passwords at http://FAQ.IIAB.IO) to click Install Content (on top) > Get Map Region (on the left).

3. Pick a checkbox on the left to download, unpack and install the Map Region (Map Pack) you want.  As you hover (mouse over) the choices on the left, colorful bounding boxes light up on the world map on the right &mdash; to help you choose the Map Pack most suitable for your region:

   - As of June 2019 you can choose among the major continents, Central America (3.77 GB), the Middle East (7.66 GB) or the World (53.17 GB).

4. After making your choice, kick off your Map Pack download/installation using the 'Install Selected Region' button:

   - Please be patient as this can sometimes take a few hours, depending on your Internet connection etc!  You can monitor the progress by clicking Utilities (on top) > Display Job Status (on the left).

   - Here's a working example/sample of IIAB maps in action, so you know how they'll appear after your chosen Map Pack installs itself, including fully-zoomable details for all continents in this case: http://iiab.me/maps

5. Once your Map Pack is installed, try it out at http://box/maps &mdash; and also look over your new IIAB home page (typically http://box, or http://172.18.96.1, or http://box.local) where a new Content Pack should appear, briefly describing the Map Pack you installed &mdash; for students and teachers to click on!

## How do I upgrade an IIAB Map Pack?

In the weeks/months after installing your IIAB Map Pack, you might have noticed that a new one was published, by perusing these "map catalog" links showing the latest available:

- https://archive.org/search.php?query=osm-vector&sort=-publicdate
- http://download.iiab.io/content/OSM/vector-tiles/maplist/assets/regions.json
- https://github.com/georgejhunt/maps/blob/new-bboxes/resources/regions.json _(out of date?)_
- https://github.com/iiab/maps/blob/master/osm-source/ukids/assets/regions.json _(out of date?)_

Just for now (as of June 2019, for IIAB 7.0) the process of upgrading to the latest IIAB Map Pack needs to be done manually:

1. Back up your Internet-in-a-Box (IIAB) using one of the techniques described in http://FAQ.IIAB.IO > "How do I back up, shrink & copy IIAB microSD cards?"
2. Delete your existing/installed Map Pack from within `/library/www/osm-vector-maps` &mdash; this will be a directory like en-osm-omt_africa_2017-07-03_v0.2 that typically contains many gigabytes
3. Use a text editor like nano to remove the deleted Map Pack's stanza from `/library/www/html/common/assets/vector-map-idx.json`
4. Run this 7-line recipe to upgrade all your IIAB software:

    ```
    sudo su -

    cd /opt/iiab/iiab
    git pull
    ./iiab-install --reinstall    # takes about 20+ min (or run "./runrole osm-vector-maps" which is faster)

    cd /opt/iiab/iiab-admin-console
    git pull
    ./install                     # takes about 3-5 min
    ```

5. Follow the original instructions above ("How do I install an IIAB Map Pack for my region?") i.e. http://box.lan/admin > Install Content > Get Map Region
6. Clean up or [customize your IIAB home page](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_customize_my_Internet-in-a-Box_home_page.3F) (http://box) as necessary.

## What might future IIAB Maps bring?

_INVITATION: If you can help ongoing efforts to polish maps for children in offline schools in all countries, directly contributing to [beautifying OpenStreetMap (VIDEO)](https://youtu.be/HJub6U_U7Mg) thereby bringing Earth to life for all, Thank You!  Read more at ([#877](https://github.com/iiab/iiab/issues/877#issuecomment-405935272)) and please do [get in touch](#What_are_the_best_places_for_community_support.3F) to learn more!_

_Thanks for your help evolving this into a continuously more friendly community product, as Usability Engineering begins right here &mdash; thanks to all who can assist!  Background: Internet-in-a-Box is a [volunteer community](http://internet-in-a-box.org/pages/contributing.html) that greatly welcomes your suggestions and contributions !_

- https://github.com/iiab/iiab/issues?q=is%3Aopen+OSM
- Description of Map Packs (on your http://box IIAB Home Page) could offer more tips & tricks for teachers and students, e.g. how to search for cities etc
- http://box/maps/maplist/ might show more of a visual catalog of what maps were available around the time your IIAB was originally installed, or most recently updated?
- Please [suggest](http://wiki.laptop.org/go/IIAB/FAQ#What_are_the_best_places_for_community_support.3F) something!

Thank you to George Hunt, Tim Moody, Adam Holt, Anish Mangal, Avni Khatri, Mir Rodríguez Lombardo & others who made this all possible so far!

## Software (Source Code)

- https://github.com/iiab/maps
- https://github.com/iiab/iiab/tree/master/roles/osm-vector-maps

## Links & Advanced Topics

- [FAQ.IIAB.IO](http://FAQ.IIAB.IO) > ["How do I add zoomable maps for my region?"](http://FAQ.IIAB.IO#How_do_I_add_zoomable_maps_for_my_region.3F)
- History And Architecture: https://github.com/iiab/maps/blob/master/docs/README.md
- "Make your own IIAB Map Pack" notes are emerging: https://github.com/georgejhunt/maps/blob/simple/generate-regions/readme.md
- Original Design 1: https://github.com/georgejhunt/iiab-factory/blob/vector-maps/content/vector-tiles/Design-Decisions.md
- Original Design 2: https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/Design-Decisions.md
- "Package up vector-based OSM maps" task list: https://github.com/iiab/iiab/issues/877#issuecomment-405935272
- Living Docs for IIAB 7.0 Maps: https://github.com/iiab/iiab/issues/1710