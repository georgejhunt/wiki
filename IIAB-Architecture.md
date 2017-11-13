# Internet-in-a-Box (IIAB) Architecture

## Anatomy 101: Critical Server Internals & Configuration Overview

Building an IIAB server requires a number of steps, and there is usually some configuration required at each step:

  1. Choice of OS (operating system), keyboard layout, disk format, and partitioning. IIAB has [partitioning requirements](https://github.com/iiab/iiab/wiki/IIAB-Platforms#disk-partitioning).

  2. IIAB takes over after the OS is functioning on the target hardware. This step is usually done at a terminal console or via a ssh remote connection to the newly installed OS. (If all the requirements are in place, this step can be as simple as typing "cd /opt/iiab/iiab" then "./iiab-install", formerly "./runansible").

 There is some automatic configuration built into IIAB, during this text mode phase. There will almost always be a network connection to the internet left over from the first step. If a second Ethernet or Wi-Fi adapter is discovered, "Gateway" mode will be chosen.  If not, the mode selected will be "Appliance". See the [Networking document](https://github.com/iiab/iiab/wiki/IIAB-Networking) which reviews **three possible modes of operation.**

 There is also the option of setting a large array of variables that govern the detailed installation process. In most cases, the supplied defaults will be sufficient. Any changes to defaults should be placed in [``./vars/local_vars.yml``](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F) within /opt/iiab/iiab (See details of [variable precedence](#variable-precedence) below).

  3. The Admin Console is the Graphical User Interface (when you log in to [http://box/admin](http://box/admin)) for making most configuration changes.  There is also a HELP menu system in the Admin Console itself, reproduced in full here:
     1. [Overview](https://github.com/iiab/iiab-admin/blob/master/roles/console/files/help/Overview.rst)
     2. [Control](https://github.com/iiab/iiab-admin/blob/master/roles/console/files/help/Control.rst)
     3. [Configuration](https://github.com/iiab/iiab-admin/blob/master/roles/console/files/help/Config.rst)
     4. [Install Content](https://github.com/iiab/iiab-admin/blob/master/roles/console/files/help/InstContent.rst)
     5. [Utilities](https://github.com/iiab/iiab-admin/blob/master/roles/console/files/help/Utilities.rst)

By default, most software required by the IIAB server is installed during the text mode (step #2), but not enabled.  Then the enabling of services, and loading of content, is done during step #3.

### Detailed Description of Ansible control variables

Please see the [IIAB Variables](https://github.com/iiab/iiab/wiki/IIAB-Variables) document, for a more comprehensive take than the 2 sections below.

The ./vars/default_vars.yml (typically within /opt/iiab/iiab) is the first place to look for variables that might control the install process. But the place to make any changes is in ./vars/local_vars.yml. Any variable assignments you make in local_vars.yml will override values in default_vars.yml

In general, there is a ``<role name>_install`` and a ``<role name>_enabled`` variable for each role. (The roles can be found in the directories under /opt/iiab/iiab/roles/). For most roles, during the text mode install phase, the install variable is set to ``True``, and the enabled variable is set to ``False``.

#### Variable Precedence
There is a hierarchy of places to define variables in Ansible, _progressing from lowest precedence to highest:_

  1. The setup module explores hardware, and defines a large number of variables. All of these have the prefix: "ansible_".
  2. Variable defaults can be set in each role, with the existence of a ``<role name>/defaults/main.yml`` file.
  3. At the root of the repo, there is a [``./vars/default_vars.yml``](https://github.com/iiab/iiab/blob/release-6.2/vars/default_vars.yml) which gives initial values for repo wide settings, and also many role specific ones. **Note:** this file may be overwritten by later releases, and should not be modified by the end user.
  4. Operators should place changes in [``./vars/local_vars.yml``](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F) in /opt/iiab/iiab using a text editor such as vi, nano, or emacs.  Remember to then run "cd /opt/iiab/iiab" followed by "./iiab-install --reinstall", formerly "./runansible" (takes ~30min to complete on RPi3, done!)  Or, the essential 6 "post-install" roles of Ansible's 9 overall roles can be run from Admin Console (http://box/admin) -> Configure menu -> Install Configured Options button. Then monitor the progress (~25min on RPi3) within Utilities menu -> Display Job Status.
  5. Changes made in the Admin Console ([http://box/admin](http://box/admin)) take precedence over all above &mdash; **this is the preferred place for field operators to make changes.**  Remember to enact these changes, using Configure menu -> Install Configured Options then monitor/confirm within Utilities menu -> Display Job Status (~25min on RPi3).

### Documentation

A growing collection of Internet-in-a-Box [technical support docs](http://wiki.laptop.org/go/IIAB/FAQ#What_technical_documentation_exists.3F) (and eventually videos) are being made available for offline users as well, at [http://box/info](http://box/info)