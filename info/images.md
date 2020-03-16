## Which ***Internet In A Box* (IIAB) Image is Best for Me?

### Raspbian Lite
 
#### Pros
1. Runs best on low powered hardware like the RPi W.
2. Small Size. Does not compete for SD card space with content.
3. Does not compete for memory that might otherwse be used by a Graphical User Interface (GUI).
4. Raspbian supplies a text mode configuration utility (raspi-config) which simplifies many tasks.
5. If used on a RPi-W, the lower hardwaare performance limits the number of clients.
#### Cons
1. Configuration requires more knowledge, and more text editing, to set up some of the services.
2. No GUI. Most computer users are familiar with the GUI supplied by Windows, Mac, or Linux operating systems.
3. New users will find it more difficult to explore what Raspbian offers without a GUI and menus. 

### Raspbian Full
#### Pros
1. The GUI and menuing system showcases the services and functions of the Raspbian Operating System.
2. Skills learned on other Operating Systems transfer more easily during IIAB setup.
3. There is a wide selection of programs which permit using this image as a stand alone computer. The image is dual purpose, as both a client and as a server.
4. Realvnc has apparently licensed their remote desktop server to Raspberry Pi Foundation. This version of the VNC server provides a WiFi remote GUI connection. It lets clients authendicate via regular linux user/password credentials which greatly simplifies  server security.
5. As a first trial run, this image greatly simplifies setting up a Raspberry pi, and trying IIAB. It eliminates the need for separate purchase of a monitor, keyboard, mouse, and the miscellaneous video cables -- assuming that a VNC viewer can be installed on the laptop or desktop used to download images and copy them to SD cards.

#### Cons
1. Compared with the Lite image (4GB), it uses more than twice as much SD card (11GB).
1. The GUI uses about 200KB of memory. This is more of an issue with early RPi's that had 256MB or 512MB, compared with the RPi 4 which comes with 1GB, 2GB, or 4GB of memory.
1. If used as a teacher's computer at the front of the classroom, it's use as a reqular computer might might unintentionally contribute to less reliable server performance for the whole classroom.
1. The RPi3+ has been verified to function with 24 WiFi clients, but on a RPi4 the limit appears to be 18 connections.

### Ubuntu
#### Pros
1. The 64bit Operating system appears to be about 15 percent faster.
1. More clients.Ubuntu has been verified to support 32 simultaneous WiFi clients.

#### Cons
1. The ease of use of Raspbian, advanced by the continuous refinement and feedback from 11 million users, is not available. The best example of this is the lack of ```raspi-config``` which permits easy refinement of a downloaded image in either text and graphical mode.
1. VNC is much more difficult to set up, to make secure, and not provided in this image. It is possible to take advantage of the secure remote access provided by ```ssh``` (secure shell). But it requires changes to the way "secure shell" is set up and used.

