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

As of 2019 the menu is defined by a file `menu.json` located in the same directory as `index.html`. The menu.json file contains properties for the menu as a whole and a list of menu items to be included as links on the menu. For most installations these files are in `/library/www/html/home`, but they can be anywhere and the index.html file can be named anything (e.g. /test/medlib.html). When using IIAB's Admin Console (http://box.lan/admin) you can click on [Help (top-right) > Content Menus > Edit Content Menus](https://github.com/iiab/iiab-admin-console/blob/master/roles/console/files/help/ContentMenus.rst#edit-content-menus) to learn more about the menu.json fields.

Bonus: if users prefer http://box.lan, http://172.18.96.1, http://box.local or [http://hogwarts](http://hogwarts) (or any other base URL that works, as your network topology evolves) then important ports like kiwix-serve's 3000 and KA Lite's 8008 continue to work, as they are updated live by JavaScript inside the HTML, e.g. to [http://hogwarts:3000](http://hogwarts:3000) and [http://hogwarts:8008](http://hogwarts:8008)

As of 2019 the source for the menuing system is part of the git repo for the Admin Console, named [iiab-admin-console](https://github.com/iiab/iiab-admin-console) and is installed when the install script for Admin Console is run. There are several sample menus that can be copied as is to /library/www/html/home if you are using the /home home page redirect selection.

## Menu Item Definitions

A menu item definition consists of a json and an optional html fragment file, which more or less follow the RACHEL conventions on naming modules:

<2 char lang code of menu item (may be different from content)>\-\<generic zim or module name which may have inherent language embedded in it; must separate parts with underscores\>.json

e.g. kn-wikipedia_kn_medicine.json is a menu item for the medical wiki in the Kannada language, where the title and description are (theoretically) in Kannada, whereas en-wikipedia_kn_medicine.json would be an English menu item for the Kannada medical wiki.  In future we may have a CMS that allows these to be selected visually and edited, but for now the easiest method is to browse index-dynamic.html and get the name from the generated html.  **More or less all names are in content-ready-index.html, though they have been commented out to reduce clutter.**

After installation these files will be in `/library/www/html/js-menu/menu-files/menu-defs`

There is a separate directory /library/www/html/js-menu/local in which locally modified versions of these files may be stored so that they will not be overwritten when cp-menus is run, but will instead be merged in.

**Please note** that this is a work in progress with new menu definitions being added as deployments need them.

## HTML Fragments

The html fragments are mostly extracted from RACHEL and are all \<ul\>\</ul\> structures, but they can be created manually as long as they don't break Ajax.  The php href code was replaced with ##HREF-BASE## when the file was extracted from rachel-index.php and is dynamically rewritten with the appropriate href at run time.

## Menu Item Definition Fields

Earlier (in 2017) [_menudef-template.json](https://github.com/iiab/iiab-menu/blob/master/samples/_menudef-template.json) was used to explain these various fields.

As of mid-2019 Menu Item Definition files have the following fields:

* intended_use - May be one of zim, html, webroot, external, kalite, kolibri, cups, nodered, calibre, calibreweb, info, download
* lang - 2 or 3 char code of the language of the menu item, not necessarily the target content
* logo_url - An image file in `/library/www/html/js-menu/menu-files/images`
* moddir - The name of a directory under <webroot>/modules, for intended_use webroot or download it is relative to <webroot>
* zim_name - The generic name of a Kiwix ZIM, such as wikipedia_en_all_novid
* start_url - Optional url for link to be added to the computed link, used mostly when a module has no index.html
* title - Localized title for link
* description - Expanded text for link
* extra_description - More expanded text for link
* extra_html - Nominally <menu_item_name>.html, an optional free form html for a submenu
               be careful of embedded quotes, brackets or other characters that will break json
* footnote - Catalog entry type information such as number of pdfs or size
* apk_file - This is no longer used; use the download type for downloading apks and other files

You may also notice that there are menu definitions with additional properties. These have been taken from RACHEL catalog and are information only fields, not used by the IIAB menuing system. They will be removed over time.

## Config File

As of December, 2017 the IIAB menuing system has a configuration file, \<docroot\>/js-menu/config.json , with the following properties that are used to compute URLs dynamically:

* kiwixPort          - Port on which kiwix is listening
* en-kalitePort      - Port on which kalite is listening  
* es-kalitePort      - Alternate Port for kalite to serve content in Spanish
* fr-kalitePort      - Alternate Port for kalite to serve content in French

Multiple instances of KA Lite may be run to separate content by language (with the caveat that KA Lite itself uses a shared cookie, so a browser cannot log into these multiple instance at the same time)<!-- when not using registered users-->.  For implementation tips, see: http://FAQ.IIAB.IO -> "KA Lite Administration: What tips & tricks exist?" -> "Multilingual?" | "Monolingual in Spanish or French or similar?"

* calibrePort        - Port on which calibre is listening  
* apkBaseUrl         - URL where downloadable APKs are stored; used by download phrase in Medical Wikis 
* apkLocalUrl        - Not used, but serves to preserve the URL in the local server  
* apkLinkPhrase      - An array with the phrase 'Download the offline app' in various languages  
* mobilePortraitSize - Font size for mobile devices in portrait orientation
* poweroffPin        - Not Used
* poweroffPinHash    - Not Used
* kiwixUrl           - Prefix to URL for ZIM files when running kiwix in proxy mode

## 2019 Additions

Log in to IIAB's Admin Console (http://box.lan/admin, default passwords are in http://FAQ.IIAB.IO) then click "Content Menus" on top:

1) Drag & Drop your favorite Content Packs into position, to create the best visual menu for your school or medical clinic's Internet-in-a-Box. 
2) Services installed are automatically added to the menu during Ansible run for Admin Console.
3) Downloaded ZIM files and OER2GO modules are automatically added to the menu.
4) Draft menu item definitions are generated if they don't exist.
5) Additional substitution variables are now available ##SIZE##, Articles: ##ARTICLE_COUNT##, Media: ##MEDIA_COUNT##, Tags; [##tags##], Language: ##language##, Date: ##zim_date##"
6) Cross-ZIM search can be enabled for the menu.
7) Menu supports filtering by language.
8) Verbosity for desktop and mobile layouts can be configured.
9) There is a choice of header font for desktop and mobile layouts.
10) Individual Menu Item Definitions can be edited.
11) New Menu Item Definitions can be created using the Clone button.
12) There are two new check boxes to indicate if your changes should be uploaded to the central repository and if you want to receive changes from others. 

While using IIAB's Admin Console (http://box.lan/admin) please also click on "Help" in the top-right, a copy of which is here:  
https://github.com/iiab/iiab-admin-console/blob/master/roles/console/files/help/ContentMenus.rst

## Testing or Non-production Use

Please put the following in /etc/iiab/local_vars.yml so edits do not go into the production repository:

menu_files_repo : iiab-share/js-menu-files-test/