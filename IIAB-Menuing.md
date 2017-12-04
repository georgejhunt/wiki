# Internet-in-a-Box (IIAB) Menuing

## Overview

IIAB has several different approaches to the home page or portal, accessed via the following URLs:

* http://\<host\>/home/index.html - dynamically generates a menu of your Content Packs (see _Dynamic Menuing_ below)

* http://\<host\>/wordpress - if installed and enabled WordPress can be used as the home page.

* http://\<host\>/wiki - if installed and enabled a wiki, currently DokuWiki, can be used as the home page.

Any one of these can be selected using the Admin Console option Configure->Server Portal. A redirect from http://\<host\>/ is created to the URL selected.

## Dynamic Menuing instead of hand coding index.html

Dynamic Menuing (introduced with IIAB/XSCE 6.1, improved with IIAB/XSCE 6.2) allows you to rapidly rearrange the presentation of all your Content Packs &mdash; so they appear as your school/library/clinic community wants &mdash; when users browse [http://box](http://box).  Dynamic Menuing uses JavaScript to auto-generate this menu of Content Packs, based on an array of menu items.

The menu is determined by an array at the top of index.html, which is expected to be /library/www/html/home/index.html, but can be anywhere and can be named anything (e.g. /test/medlib.html).

Bonus: if users prefer http://box.lan, http://172.18.96.1 or [http://hogwarts](http://hogwarts) (or any other base URL that works, as your network topology evolves) then important ports like kiwix-serve's 3000 and KA Lite's 8008 continue to work, as they are updated live by JavaScript inside the HTML, e.g. to [http://hogwarts:3000](http://hogwarts:3000) and [http://hogwarts:8008](http://hogwarts:8008)

The source for the menuing system is in a git repo named [iiab-menu](https://github.com/tim-moody/iiab-menu) (in future at [github.com/iiab/iiab-menu](https://github.com/iiab/iiab-menu)), which must be cloned to /opt/iiab-menu (most [downloadable images](http://download.iiab.io) have this already done). That repo contains a script **cp-menus** to install the requisite files and dependencies. There are several sample menus that can be copied as is to /library/www/html/home/index.html if you are using the /home home page redirect selection.

## Menu Definitions

A menu item definition consists of a json and an optional html fragment file, which more or less follow the RACHEL conventions on naming modules:

<2 char lang code of menu item (may be different from content)>\-\<generic zim or module name which may have inherent language embedded in it; must separate parts with underscores\>.json

e.g. kn-wikipedia_kn_medicine.json is a menu item for the medical wiki in the Kannada language, where the title and description are (theoretically) in Kannada, whereas en-wikipedia_kn_medicine.json would be an English menu item for the Kannada medical wiki.  In future we may have a CMS that allows these to be selected visually and edited, but for now the easiest method is to browse index-dynamic.html and get the name from the generated html.  **More or less all names are in content-ready-index.html, though they have been commented out to reduce clutter.**

There is also a menu-def json file named _menudef-template.json which has the various fields with comments.

After cp-menus has run these files will be in **/library/www/html/iiab-menu/menu-files/menu-defs**

There is a separate directory /library/www/html/iiab-menu/local in which locally modified versions of these files may be stored so that they will not be overwritten when cp-menus is run, but will instead be merged in.

**Please note** that this is a work in progress with new menu definitions being added as deployments need them.

## HTML Fragments

The html fragments are mostly extracted from RACHEL and are all \<ul\>\</ul\> structures, but they can be created manually as long as they don't break Ajax.  The php href code was replaced with ##HREF-BASE## when the file was extracted from rachel-index.php and is dynamically rewritten with the appropriate href at run time.

## Menu Definition Template

Here is the template as of March 2017:

    {
    "intended_use" : "", // must be one of zim, html, webroot, osm, kalite
    "lang" : "en", // 2 or 3 char code of language of content; may be different from menu item
    "logo_url" : "", // assumed to be relative to /common/images
    "menu_item_name" : "", // MUST be the name of this file (without .json); is the unique, logical name of this menu item, e.g. en-wikipedia_ar_all, ar-osm, en-hesperian
    "moddir" : "", // for html modules is the directory under /modules
    "start_url" : "" // optional suffix to base href without leading slash
    "zim_name" : "", // generic zim name with out YYYY-MM version suffix
    "title" : "", // localized title for link
    "description" : "", // expanded text for link
    "extra_html" : "<menu_item_name>.html", // optional free form html for submenu or other use
                   // be careful of embedded quotes, brackets or other characters that will break json
    "apk_file" : "<apk file without full path>" // optional
    }