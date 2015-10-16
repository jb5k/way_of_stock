New Computer Checklist
======================

Create User
-----------

Chrome
------
[Download](http://www.google.com/chrome/)

Java 7
------
[Download](https://s3-ap-southeast-2.amazonaws.com/stocksoftware-installers/jdk7/mac/jdk-7u79-macosx-x64.dmg)

Java 8
------
Currently only required for ARENA development.

Libre Office
------------

VPN
---
[Download Cisco AnyConnect mobility client 3.1](https://s3-ap-southeast-2.amazonaws.com/stocksoftware-installers/CiscoAnyConnect/mac/anyconnect-macosx-i386-3.1.06079-k9.dmg)

Slack
-----

Source Tree (Mac only)
----------------------

Keepass 2.30
------------
[Download](http://keepass.info/download.html) (requires Mono and XQuartz on a Mac)


Set up Localhost (Mac only)
----------------
You may run into problems when connecting to the VPN whereby your localhost turns into something unrecognisable.  If this happens issue the following command replacing computer_name with your machines name e.g. 'Karens-MacBook-Pro':-
```sh
sudo scutil --set HostName <computer_name>.local
```
