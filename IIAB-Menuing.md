# Internet-in-a-Box (IIAB) Menuing

Please see "[How do I customize my Internet-in-a-Box home page?](http://wiki.laptop.org/go/IIAB/FAQ#How_do_I_customize_my_Internet-in-a-Box_home_page.3F)" within [FAQ.IIAB.IO](http://FAQ.IIAB.IO) which links to several videos, to help you quickly arrange the content and apps/services on your community's IIAB home page, using our new drag-and-drop interface.

## Overview

IIAB has several different approaches to the home page or portal, accessed via the following URLs:

* http://\<host\>/home/index.html - dynamically generates a menu of your Content Packs (see _Dynamic Menuing_ below)

* http://\<host\>/wordpress - if installed and enabled WordPress can be used as the home page.

* http://\<host\>/wiki - if installed and enabled a wiki, currently DokuWiki, can be used as the home page.

Any one of these can be selected using the Admin Console option Configure->Server Portal. A redirect from http://\<host\>/ is created to the URL selected.

## Dynamic Menuing instead of hand coding index.html

Dynamic Menuing (introduced with IIAB/XSCE 6.1, improved with IIAB/XSCE 6.2) allows you to rapidly rearrange the presentation of all your Content Packs &mdash; so they appear as your school/library/clinic community wants &mdash; when users browse [http://box](http://box).  Dynamic Menuing uses JavaScript to auto-generate this menu of Content Packs, based on an array of menu items and other properties.

As of 2019 the menu is defined by a file menu.json located in the same directory as index.html. That file contains properties for the menu as a whole and a list of menu items to be included as links on the menu. For most installations these files are in /library/www/html/home, but they can be anywhere and the index.html file can be named anything (e.g. /test/medlib.html). While using IIAB's Admin Console (http://box.lan/admin) please also click on "Help" in the top-right to learn more about the menu.json fields.

Bonus: if users prefer http://box.lan, http://172.18.96.1 or [http://hogwarts](http://hogwarts) (or any other base URL that works, as your network topology evolves) then important ports like kiwix-serve's 3000 and KA Lite's 8008 continue to work, as they are updated live by JavaScript inside the HTML, e.g. to [http://hogwarts:3000](http://hogwarts:3000) and [http://hogwarts:8008](http://hogwarts:8008)

As of 2019 the source for the menuing system is part of the git repo for the Admin Console, named [iiab-admin-console](https://github.com/iiab/iiab-admin-console) and is installed when the install script for Admin Console is run. There are several sample menus that can be copied as is to /library/www/html/home if you are using the /home home page redirect selection.

## Menu Item Definitions

A menu item definition consists of a json and an optional html fragment file, which more or less follow the RACHEL conventions on naming modules:

<2 char lang code of menu item (may be different from content)>\-\<generic zim or module name which may have inherent language embedded in it; must separate parts with underscores\>.json

e.g. kn-wikipedia_kn_medicine.json is a menu item for the medical wiki in the Kannada language, where the title and description are (theoretically) in Kannada, whereas en-wikipedia_kn_medicine.json would be an English menu item for the Kannada medical wiki.  In future we may have a CMS that allows these to be selected visually and edited, but for now the easiest method is to browse index-dynamic.html and get the name from the generated html.  **More or less all names are in content-ready-index.html, though they have been commented out to reduce clutter.**

There is also a menu-def json file named _menudef-template.json which has the various fields with comments.

After installation these files will be in **/library/www/html/js-menu/menu-files/menu-defs**

There is a separate directory /library/www/html/js-menu/local in which locally modified versions of these files may be stored so that they will not be overwritten when cp-menus is run, but will instead be merged in.

**Please note** that this is a work in progress with new menu definitions being added as deployments need them.

## HTML Fragments

The html fragments are mostly extracted from RACHEL and are all \<ul\>\</ul\> structures, but they can be created manually as long as they don't break Ajax.  The php href code was replaced with ##HREF-BASE## when the file was extracted from rachel-index.php and is dynamically rewritten with the appropriate href at run time.

## Menu Definition Template

Here is the template as of March 2017:

    {
    "intended_use" : "", // must be one of zim, html, webroot, osm, kalite
    "lang" : "en", // 2 or 3 char code of language of content; may be different from menu item
    "logo_url" : "", // assumed to be relative to /common/images
    "menu_item_name" : "", // OPTIONAL. If present, this MUST correspond exactly to the name of this file (but without its .json suffix). This is the unique, logical name of this menu item, e.g. en-wikipedia_ar_all, ar-osm, en-hesperian
    "moddir" : "", // for html modules is the directory under /modules
    "start_url" : "" // optional suffix to base href without leading slash
    "zim_name" : "", // generic ZIM name with out YYYY-MM version suffix
    "title" : "", // localized title for link
    "description" : "", // expanded text for link
    "extra_html" : "<menu_item_name>.html", // optional free form html for submenu or other use
                   // be careful of embedded quotes, brackets or other characters that will break json
    "apk_file" : "<apk file without full path>" // optional
    }
You may also notice that there are menu definitions with additional properties. These have been taken from RACHEL catalog and are information only fields, not used by the IIAB menuing system.

## Config File

As of December, 2017 the IIAB menuing system has a configuration file, \<docroot\>/js-menu/config.json , with the following properties that are used to compute URLs dynamically:

* kiwixPort          - Port on which kiwix is listening
* en-kalitePort      - Port on which kalite is listening  
* es-kalitePort      - Alternate Port for kalite to serve content in Spanish
* fr-kalitePort      - Alternate Port for kalite to serve content in French

Multiple instances of kalite may be run to separate content by language when not using registered users.
* calibrePort        - Port on which calibre is listening  
* apkBaseUrl         - URL where downloadable APKs are stored; used by download phrase in Medical Wikis 
* apkLocalUrl        - Not used, but serves to preserve the URL in the local server  
* apkLinkPhrase      - An array with the phrase 'Download the offline app' in various languages  
* mobilePortraitSize - Font size for mobile devices in portrait orientation
* poweroffPin        - Not Used
* poweroffPinHash    - Not Used
* kiwixUrl           - prefix to URL for ZIM files when running kiwix in proxy mode

## 2019 Additions

Log in to IIAB's Admin Console (http://box.lan/admin, passwords are in http://FAQ.IIAB.IO) then click "Content Menus" on top:

1) Drag & Drop your favorite Content Packs into position at http://box to create the best visual menu for your school or medical clinic's Internet-in-a-Box. 
2) Services installed are automatically added to the menu during Ansible run for Admin Console.
3) Downloaded ZIM files and OER2GO modules are automatically added to the menu.
4) Draft menu item definitions are generated if they don't exist.
5) Additional substitution variables are now available ##SIZE##, Articles: ##ARTICLE_COUNT##, Media: ##MEDIA_COUNT##, Tags; [##tags##], Language: ##language##, Date: ##zim_date##"
6) Cross-ZIM search can be enabled for the menu.
7) Menu supports filtering by language.
8) Verbosity for desktop and mobile layouts can be configured.
9) There is a choice of header font for desktop and mobile layouts.

While using IIAB's Admin Console (http://box.lan/admin) please also click on "Help" in the top-right, a copy of which is here:  
https://github.com/iiab/iiab-admin-console/blob/master/roles/console/files/help/ContentMenus.rst