# Internet-in-a-Box (IIAB) Networking

IIAB has [three possible modes of operation](https://github.com/iiab/iiab/wiki/IIAB-Installation#supported-network-modes):

* **Appliance** - allows your server to behave like any other computer in the network, exposing the configured services. 
 Can have a single network interface (we refer to this as the 'WAN', whether or not it can reach the Internet).
* **Gateway** - allows for creating a local area network, including dhcpd, content filtering using Squid, DansGuardian and traffic shaping.  Requires two or more network interfaces ('WAN' side and 'LAN' side).
* **LAN Controller** - allows for creating a local area network, only configures DNS and dhcpd services.  Can have a single network interface (we refer to this as the 'LAN').

The install by default finds the WAN device, defaulting to the "Appliance" mode.
The install will try to find other devices for use with the LAN and if found
defaults to "Gateway" mode. You need to make some adjustments to be able to use
"LAN Controller" as it will use all available [network interfaces](https://github.com/iiab/iiab/wiki/IIAB-Platforms#network-adapters).

### Know Your Topology (and IP Addresses)

The IP address of the WAN device will normally be assigned by whatever device manages your network, though it is possible to set a fixed address.  The LAN in both Gateway and LAN Controller modes is a bridge with one or more devices, and always has the IP address 172.18.96.1, a legacy of the practice established by OLPC.  Remember, as some are confused by this, that 172.18.96.1 (AKA box.lan, or simply box) is not visible on the WAN side &mdash; but only on the LAN side &mdash; and will be used by all devices in the bridge whether wireless or wired.

WARNING: before running IIAB's [network](https://github.com/iiab/iiab/tree/master/roles/network#network-readme) role (which is part of installing IIAB) you need to connect your routers / access points per their final "in-field" configuration, and ensure they're all turned on!

EXAMPLE: If you're going to use a wired Ethernet on the LAN-side (i.e. as a slave to the br0 bridge, for client devices) it needs to be connected during IIAB's install.  ADDITIONAL WARNING: if that wired Ethernet LAN is not connected during boot, you may experience a 2-minute delay similar to [#1634](https://github.com/iiab/iiab/pull/1634) after IIAB is installed.

### List of Ports / Services

Many of the port numbers below can be changed when installing IIAB.  If you need to do this, look over the default ports in [default_vars.yml](https://github.com/iiab/iiab/blob/master/vars/default_vars.yml), and then override those that are necessary within [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F)

|Protocol  | Port                          |Service                                  |
|:--------:|:-----------------------------:|-----------------------------------------|
| TCP      | 22                            | sshd                                    |
| TCP      | 80                            | web server                              |
| UDP      | 137, 138                      | samba                                   |
| TCP      | 139, 445                      | samba                                   |
| TCP      | 631                           | cups (printing)                         |
| TCP      | 873                           | xinetd (xs-rsync, for legacy XOs)       |
| TCP      | 1880                          | nodered                                 |
| TCP      | 1883                          | mosquitto                               |
| TCP      | 3000                          | kiwix-serve                             |
| TCP      | 3128                          | squid / dansguardian                    |
| TCP      | 3130                          | squid                                   |
| TCP      | 4244                          | internetarchive                         |
| TCP      | 4369, 5222, 5223, 5280, 47893 | ejabberd OR ejabberd-xs                 |
| TCP      | 5060, 5160, 5161, 10000-20000 | pbx (Asterisk & FreePBX)                |
| UDP      | 5353                          | avahi, mDNS, bonjour                    |
| TCP      | 8006                          | kalite-serve-fr                         |
| TCP      | 8007                          | kalite-serve-es                         |
| TCP      | 8008                          | kalite-serve (English & others)         |
| TCP      | 8009                          | kolibri                                 |
| TCP      | 8010                          | calibre-serve (if avoiding idmgr/8080)  |
| TCP      | 8080                          | calibre-serve OR idmgr (for legacy XOs) |
| TCP      | 8083                          | calibre-web                             |
| TCP      | 8089                          | sugarizer                               |
| TCP      | 9091, 51413                   | transmission (BitTorrent downloader)    |
| TCP      | 27018                         | mongodb (if used by Sugarizer)          |
| UDP      | 30000                         | minetest (open source Minecraft clone)  |

### Firewall (iptables)

On the LAN side, all ports except for [databases ports](https://github.com/iiab/iiab/blob/master/roles/network/templates/gateway/iiab-gen-iptables#L104-L116) are generally open.

On the WAN side, "campus access" to [~10 common IIAB services](https://github.com/iiab/iiab/blob/master/roles/network/templates/gateway/iiab-gen-iptables#L140-L161) like Kiwix (3000), KA Lite (8008) and Calibre (8010 or 8080) is enabled by default.  Override this default by uncommenting **just one** of the following lines in [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F):

    #ports_externally_visible: 0 # none
    #ports_externally_visible: 1 # ssh only
    #ports_externally_visible: 2 # ssh + http-or-https (for Admin Console's box.lan/admin too)
    ports_externally_visible: 3  # ssh + http-or-https + common IIAB services  <--  DEFAULT
    #ports_externally_visible: 4 # ssh + http-or-https + common IIAB services + Samba
    #ports_externally_visible: 5 # all but databases

If your IIAB is already installed, run `cd /opt/iiab/iiab` followed by either `./runrole network` or [./iiab-network](https://github.com/iiab/iiab/blob/master/iiab-network) &mdash; to put this firewall change into effect.

If necessary, you can further customize your iptables firewall by modifying [/opt/iiab/iiab/roles/network/templates/gateway/iiab-gen-iptables](https://github.com/iiab/iiab/blob/master/roles/network/templates/gateway/iiab-gen-iptables) (part of Ansible's [network](https://github.com/iiab/iiab/tree/master/roles/network#network-readme) role, this is the template for the /usr/bin/iiab-gen-iptables command).  As above, you'd then need to run `cd /opt/iiab/iiab` followed by either `./runrole network` or [./iiab-network](https://github.com/iiab/iiab/blob/master/iiab-network) &mdash; to put your firewall changes into effect.

### DNS

DNS (name resolution) for LAN clients is generally provided by the `dnsmasq` service, unless you override that in favor of named (BIND) in [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F)

However some Linux distributions do not function well with dnsmasq's default service.  Several of these systemd unit files have a timing problem.  As a result, IIAB uses the [iiab-dnsmasq](https://github.com/iiab/iiab/blob/master/roles/network/tasks/enable_services.yml#L51-L73) service instead &mdash; to start dnsmasq at the correct time during boot.  IIAB disables the OS's stock dnsmasq unit file across all distros to be safe.

_Finally **after** your IIAB install is complete, you can monitor dnsmasq as follows:_

    systemctl status dnsmasq

#### CLARIFICATIONS:

1) dnsmasq is _disabled_ when IIAB is in Appliance mode.
2) dnsmasq provides _both DHCP and DNS server functionality_ when IIAB isn't in Appliance mode.
3) While LAN clients use dnsmasq, IIAB boxes use one of the following to get their own DNS from upstream:
```
systemctl status dhcpcd              # e.g. on Raspbian
systemctl status systemd-networkd    # e.g. on Debian 9 Stretch
systemctl status systemd-resolved    # e.g. on Debian 10 Buster, Ubuntu 18.04 (see also netplan.io, replacing ifupdown)
```
4) On Raspbian, note that (a) systemd service `wpa_supplicant` is started by the above-mentioned `dhcpcd` service (b) your building's SSID and password can be put into /etc/wpa_supplicant/wpa_supplicant.conf by running the `raspi-config` command.

### Common Customizations

(1) If you you want to hard-code a Fixed IP Address for the WAN-side of your IIAB, please see "How do I set a static IP Address?" at http://FAQ.IIAB.IO

(2) If your Internet-in-a-Box (IIAB) contains multiple Wi-Fi interfaces, put the following into [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F) to ask IIAB not to create a LAN-side access point from the wlan0 interface:

    reserved_wifi: wlan0

If "./iiab-install" has already completed, then run the following commands to (re)configure networking:
```
cd /opt/iiab/iiab/
./iiab-network     (or "./runrole network")
```
Context: IIAB code defaults to the highest numbered when setting up a Wi-Fi hotspot, e.g. IIAB would normally use wlan1 anyway, if it found both {wlan0, wlan1}.  So in this case "reserved_wifi: wlan0" just avoids ambiguity, explicitly confirming that wlan0 should remain unused by IIAB.

You'd typically do this to force wlan0 onto the WAN-side (e.g. for possible Internet access, or other purposes) of your IIAB.  Guaranteeing that your wlan1 becomes the "learning hotspot" Wi-Fi access point on the LAN-side &mdash; i.e. under the bridge (br0) &mdash; as shown by running `brctl show`.  Background at: [#531](https://github.com/iiab/iiab/pull/531#issuecomment-344963643)

(3) These 2 lines are important defaults in [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F) originating from mid-2017:

* ports_externally_visible: 3 &nbsp; &nbsp; &nbsp; &nbsp; (read [above](#firewall-iptables) to modify your firewall settings for different kinds of campuses/SOHO/families)
* iiab_gateway_enabled: False &nbsp; &nbsp; (blocks LAN-side users from reaching the Internet, while permitting them access to IIAB/local content)

If making changes to [/etc/iiab/local_vars.yml](http://wiki.laptop.org/go/IIAB/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F), remember the general rule is to then run "cd /opt/iiab/iiab" followed by "./iiab-install --reinstall" (formerly "./runansible") &mdash; which can take one or more hours on Raspberry Pi 3 &mdash; if IIAB's (Ansible-based) install process wasn't yet run.

Or, the essential [1+6 "post-install" roles](https://github.com/iiab/iiab/blob/master/iiab-from-console.yml) of Ansible's 9 overall roles can be run **far faster** from Admin Console ([http://box/admin](http://box/admin)) -> Configure menu -> Install Configured Options button. Then monitor the progress (~20 min on RPi3) in Utilities menu -> Display Job Status.  This is very similar to "./iiab-install --debug".

Read more about `local_vars.yml` within [IIAB Architecture](https://github.com/iiab/iiab/wiki/IIAB-Architecture) and our [Frequently Asked Questions](http://FAQ.IIAB.IO) under ["What is local_vars.yml and how do I customize it?"](http://FAQ.IIAB.IO#What_is_local_vars.yml_and_how_do_I_customize_it.3F)

**_Please also read "Any other networking tips?" within [FAQ.IIAB.IO](http://FAQ.IIAB.IO)_**