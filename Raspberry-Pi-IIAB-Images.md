# Raspberry Pi Images

Author: Tim Moody; Last Updated: Mar 16, 2019

You can find a growing number of **prebuilt** IIAB images on the [Internet Archive](https://archive.org/details/internetinabox). This page provides a select few to help navigate through the Internet Archive site. The images divide into three broad categories, **Generic**, **Specific Curations** and **Experimental**.

## Generic IIAB Images

The generic images are simply prebuilt versions of what you could build yourself with [curl scripts at download.iiab.io](http://download.iiab.io/). Instead of downloading a raspbian image, writing it to an sdcard, and running the curl script, you just download one of these images, write it to the sdcard, and boot IIAB.

These images are all **'Content Ready'**, that is they have a given set of services installed but no ZIMS, or OER2Go modules, or any other content and are based on 
* IIAB 6.7 with current fixes
* Raspbian Lite 2018-11-13

The three images, **min**, **medium**, and **big** are described in the [FAQ: What services (IIAB apps) are suggested during installation?](http://wiki.laptop.org/go/IIAB/FAQ#What_services_.28IIAB_apps.29_are_suggested_during_installation.3F)

Each of the links below gives a description and both torrent and download links for the particular image.

[Internet in a Box 6.7 Minimum Content Ready](https://archive.org/details/iiab-6.7-190315-min-content-ready-ga0c8314.img)

[Internet in a Box 6.7 Medium Content Ready](https://archive.org/details/iiab-6.7-190315-medium-content-ready-ga0c8314.img)

[Internet in a Box 6.7 Big Content Ready](https://archive.org/details/iiab-6.7-190315-big-content-ready-ga0c8314.img)

## Specific Curations

IIAB is deployed in a number of different countries and languages and also for a variety of audiences. Below is a selection of curations for specific environments.

### [Medical Internet in a Box Beta 3.6 Content Ready](https://archive.org/details/iiab-6.7-190314-medical-beta3.6-content-ready-ga0c8314.img)

This is also a **'Content Ready'** image but with services selected for Medical users.

### [Medical Internet in a Box South Asia Beta 2.2 (32G)](https://archive.org/details/iiab-6.4-180305-medbox-beta2.2-SAsia-32G-g3ea4256.img)

A demo of this image is available at [South Asia Demo](http://medbox.iiab.me/s-asia/).

### [Medical Internet in a Box Beta 3.1 for Nigeria 16G](https://archive.org/details/iiab-6.6-181112-medical-beta3.1-nigeria-16G-g6653593.img)

A demo of this image is available at [Nigeria Demo](http://medbox.iiab.me/medbox-ng/).

### [Medical Internet in a Box Uganda Beta 2.2 (16G)](https://archive.org/details/iiab-6.4-180313-medbox-beta2.2-uganda-16G-g3ea4256.img)

A demo of this image is available at [Uganda Demo](http://medbox.iiab.me/medbox-ug/)

### [Medical Internet in a Box Beta 3.0 Spanish (32G)](https://archive.org/details/iiab-6.4-180907-medbox-beta3.0-es-32G-g3ea4256.img)

This is an older version of Internet in a Box based on IIAB 6.4

## Experimental
Author: George Hunt; Last Updated: Mar 16, 2020

* The Raspberry Pi Foundation has recently released [rpi-imager](https://www.raspberrypi.org/blog/raspberry-pi-imager-imaging-utility/) which runs on Windows, Mac OS, and Linux. This tool makes getting started with IIAB quick and easy. 

* Once a downloaded image is written to an SD card, and running on a RPi, there are tools for updating to the most recent version, and using IIAB's browser based **Administrative Console** to download content.

### Steps to Install an Image on a RPi
1. Download and install [rpi-imager](https://www.raspberrypi.org/blog/raspberry-pi-imager-imaging-utility/) on your working laptop or desktop (needs about 50GB of free space).
2. Download and unzip the IIAB image of your choice. See [unzip suggestions](https://www.raspberrypi.org/downloads/raspbian/) in the first paragraph of the Raspbian download page.
3. Image Choices

|    OS   | Version | Bits |[IIAB Preset](http://wiki.laptop.org/go/IIAB/FAQ#What_services_.28IIAB_apps.29_are_suggested_during_installation.3F)  |  Size   | WiFi Clients | GUI   |              Features                                          |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Raspbian| Lite | 32 | Min  | 4.5GB | 24 |  NO  | Uses fewer memory and SD card resources             |
| Raspbian| Full | 32 | Med  | 11.3GB | 24 |  Optional  | GUI uses 150MB more than non-gui              |
| Ubuntu| LXDE | 64 | Min  | 7.3GB | 32 | Optional  | Faster, more clients, LXDE is 1.8GB             |


