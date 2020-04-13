## Installing RPI-IMAGER
#### Introduction -- Windows, Mac OS, Linux
Each of the three major Operating Systems has standard methods of adding programs. Raspberry Pi Foundation has developed a package they call **rpi-imager** for each of these Operating Systems. This page explains the steps that are similar in some respects, but also particular to each OS.

For each of the systems, after the normal install process, you can create a file, with the proper contents for your OS, placed in the correct place, which adds the IIAB images to the ones made available by the Raspberry Pi Foundation.

The first steps are the same for each system:
   
1. Open the browser you normally use,
1. Click on the following URL https://www.raspberrypi.org/downloads/.
1. Download the package for your OS.
1. The downloads usually go into a predefined place. But you don't usually need to know where it is, because most browsers offer a "Open in File Manager" (or "Finder") drop down option.
 
#### Windows

1. In File Manager, double click on the downloaded **rpi-image.exe** file. This will start the install process.
1. On my Windows 10 machine, after doing the install process, there is a new **rpi-imager** icon on the start menu. 
1. The easiest way to use the rpi-imager with IIAB images is to open a command prompt and paste the following into it and then press enter (make sure you include the quotes):
```
"C:\Program Files (x86)\Raspberry Pi Imager\rpi-imager.exe" --repo http://iiab.me/images.json
```
If you like you can create a .bat or .cmd file with your favorite editor in any directory you like. Just add the same line.
The following command is a little longer but does the same thing:
```
"C:\Program Files (x86)\Raspberry Pi Imager\rpi-imager.exe" --repo https://raw.githubusercontent.com/iiab/iiab-factory/master/box/rpi/iiab-imager/os_list_imagingutility.json
```

4. You can test George's images with:
```
"C:\Program Files (x86)\Raspberry Pi Imager\rpi-imager.exe" --repo https://raw.githubusercontent.com/georgejhunt/iiab-factory/testiiab/box/rpi/iiab-imager/os_list_imagingutility.json
```

4. If you created a .bat or .cmd file you can navigate to it in File Explorer and double click it.
4. Another approach is to pin rpi-imager to the task bar and then edit the icon adding one of the lines above.
4. If your .bat or .cmd file is in your path, open the command prompt, (you may need to click start, and enter "comm", and then click on the command icon).
4. Then type "imager" or whatever you called your .bat file, get the big red window, click on "OS", and verify that "IIAB" menu is at the top of the list.

#### Linux
 
 1. Open a terminal. Depending on the flavor of Linux, try "Applications" -> "System" -> "Terminal".
 2. Use the Apt package manager:
 ``` 
    cd ~/Downloads
    apt install ./rpi-imager
 ```
 3. On my ubuntu machine, this placed the **rpi-imager** in /usr/bin/rpi-imager. This directory is usually in the path for the operating system. This means that you can type **rpi-imager** located in any directory, and it will start up.
 4. But we are goint to put a little shell script into /usr/local/sbin/ which calls **rpi-imager** with a parameter which adds the IIAB menu items to the ones supplied by the rpi foundation.
 4. Use the text editor that your are familiar with to create a file with the following contents:
 ```
#!/bin/bash
# start up the rpi-imager and specify a root menu

 /usr/bin/rpi-imager --repo https://raw.githubusercontent.com/iiab/iiab-factory/master/box/rpi/iiab-imager/os_list_imagingutility.json
chmod 755  /usr/local/sbin/imager
```
1. Test your script. Type ```imager```, and click on **OS**. Success is indicated if the top menu item is an IIAB item.

#### Mac OS

1. Open the downloaded ```imager.dmg``` in **Finder** by double clicking on it.
1. In the Mac world, dragging the rpi-imager into the **Applications** folder is the normal step.
1. Execute the following lines by cutting and pasting into a terminal window (on my Mac the **Terminal.app** is in the Applications/utilities folder
```
cd   # navigate to your home directory
sudo cp "open /Applications/Raspberry\ Pi\ Imager.app/ --args --repo  https://raw.githubusercontent.com/iiab/iiab-factory/master/box/rpi/iiab-imager/os_list_imagingutility.json" > /usr/local/bin/imager
sudo chmod 755 imager
```
4. If you are wanting to use imager frequently, I find it convenient to drag the **Terminal.app** to the task bar so that it is easily available.
5. In the terminal, you will need to type ```imager```.