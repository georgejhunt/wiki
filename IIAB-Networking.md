# Internet-in-a-Box (IIAB) Networking

IIAB has [three possible modes of operation](https://github.com/iiab/iiab/wiki/IIAB-Installation#supported-network-modes):

* **Appliance** - allows your server to behave like any other computer in the network,
exposing the configured services. Can have a single network interface. 
* **Gateway** - allows for creating a local area network, including dhcpd, content
filtering using squid, DansGuardian and traffic shaping. Requires two or more
network interfaces.
* **LAN Controller** - allows for creating a local area network, excluding dhcpd,
content filtering using squid and DansGuardian and traffic shaping.
Can have a single network interface.

The install by default finds the WAN device, defaulting to the "Appliance" mode.
The install will try to find other devices for use with the LAN and if found
defaults to "Gateway" mode. You need to make some adjustments to be able to use
"LAN Controller" as it will use all available [network interfaces](https://github.com/iiab/iiab/wiki/IIAB-Platforms#network-adapters).

### IP Addresses

The ip address of the WAN device will normally be assigned by whatever device manages your network, though it is possible to set a fixed address.  The LAN in both Gateway and LAN Controller modes is a bridge with one or more devices and always has the ip address 172.18.96.1, a legacy of the practice established by OLPC. Remember, as some are confused by this, that 172.18.96.1 is not visible on the WAN, but only on the LAN, and will be used by all devices in the bridge whether wireless or wired.

### List of open ports / services

|Protocol  | Port                      |Service                                   |
|:--------:|:-------------------------:|------------------------------------------|
| TCP      | 22                        | sshd                                     |
| TCP      | 80                        | web server                               |
| TCP      | 631                       | CUPS (printing)                          |
| TCP      | 873                       | xinetd (xs-rsync, for legacy XOs)        |
| TCP      | 3000                      | kiwix-serve                              |
| TCP      | 3128                      | squid / dansguardian                     |
| TCP      | 3130                      | squid                                    |
| TCP      | 4369,47893,5280,5222,5223 | ejabberd-xs                              |
| TCP      | 8006                      | kalite-serve-fr                          |
| TCP      | 8007                      | kalite-serve-es                          |
| TCP      | 8008                      | kalite-serve (English & others)          |
| TCP      | 8010                      | calibre-server (to avoid 8080 conflicts) |
| TCP      | 8080                      | calibre-server OR idmgr (for legacy XOs) |
| TCP      | 8089                      | sugarizer                                |
| TCP      | 27018                     | mongodb                                  |

### Common Customizations

Many of us edit /opt/iiab/iiab/vars/[local_vars.yml](http://wiki.laptop.org/go/XS_Community_Edition/local_vars.yml) so it contains the following 2 lines:

* services_externally_visible: True &nbsp; &nbsp; (Opens ports over WAN/Ethernet for kiwix-serve [3000], KA Lite [8008] and calibre-server [8010] as campuses/SOHO/families often need. See the "services_externally_visible" section of [xs-gen-iptables](https://github.com/iiab/iiab/tree/master/roles/network/templates/gateway/xs-gen-iptables) if more ports are needed.)
* iiab_gateway_enabled: False &nbsp; &nbsp; (Blocks all users connecting over LAN/Wi-Fi from reaching the Internet, while still permitting them access to local content)

Note both above will likely become defaults by mid-2017.  But for now, if making changes to local_vars.yml, remember to then run "cd /opt/iiab/iiab" followed by "./runansible" (can take ~2.5 hours on RPi3).

Or, the essential [1+6 "post-install" roles](https://github.com/iiab/iiab/blob/master/iiab-from-console.yml) of Ansible's 9 overall roles can be run **far faster** from Admin Console ([http://box/admin](http://box/admin)) -> Configure menu -> Install Configured Options button. Then monitor the progress (~25min on RPi3) in Utilities menu -> Display Job Status.

Read more about `local_vars.yml` within [IIAB Architecture](https://github.com/iiab/iiab/wiki/IIAB-Architecture) and our [Frequently Asked Questions](http://FAQ.IIAB.IO) under ["What is local_vars.yml and how do I customize it?"](http://wiki.laptop.org/go/XS_Community_Edition/FAQ#What_is_local_vars.yml_and_how_do_I_customize_it.3F)