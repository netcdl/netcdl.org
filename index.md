---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
---

**NETCDL is a [DSL](https://martinfowler.com/books/dsl.html) for making assertions about networks.**


[Read the Paper](/NETCDL_thesis.pdf)

[View the Deck](/NETCDL_deck.pdf)

[Grammar Reference](/grammar)

[Certifier Implementation Guidelines](/certifier)

--------------

**Example NETCDL Document**
```
# Certification Subject: Home Network
# Author: Cody Hanson <chanson@uwalumni.com>
# Date: 10/1/2016
# Version: 1.0

define host myRouter as 192.168.1.1
define network myNetwork as 192.168.1.0/24
define network DMZ as 10.0.0.0/24
define host ftpSite as speedtest.tele2.net

link speed should be 1000Mb/s
link duplex should be full

iperf download from ent.local should be at most 30Kbps
iperf upload to ent.local should be at least 30Kbps

access vlan should be 500

dhcp server should be myRouter
dhcp dns should be myRouter
dhcp network should be 192.168.1.0/24
dhcp gateway should be 192.168.1.1

myRouter should be reachable by ping

domain name google.com should resolve using server 8.8.8.8
domain name ent.local should resolve to 192.168.1.144 using server myRouter

myRouter should be reachable on TCP port 22
myRouter should not be reachable on TCP port 23
myRouter should not be reachable on UDP port 100

#File fetch assertions, default port used for protocol, if omitted
http server at myRouter should not serve "/path/to/file" on port 8080
http server at google.com should serve "/index.html"
http server at google.com should not serve "/index.html" on port 12345

tftp server at ent.local should serve "RouterUpdate.img"
tftp server at ent.local should not serve "RouterUpdate.img.missing"

ftp server at ftpSite should serve "1KB.zip"
ftp server at ftpSite should not serve "missingfile"

traceroute to 184.99.1.89 should traverse [192.168.1.1 10.0.0.1 184.99.0.12]
traceroute to 10.0.0.1 should traverse [192.168.1.1]

packets from network DMZ should not be seen
packets from host 10.250.0.1 should not be seen
packets with type 0x18 should not be seen
packets with TCP destination port 544 should be seen
packets with TCP source port 1000 should not be seen
packets with UDP source port 1010 should be seen
packets with UDP destination port 4000 should not be seen

frames with ethertype 0x18 should not be seen
```

