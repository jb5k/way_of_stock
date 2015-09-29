New Computer Checklist
======================

Create User
-----------

Brew (Mac only)
---------------
`$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

Chrome
------
[Download](http://www.google.com/chrome/)

Git
---
Ubuntu: `$ sudo apt-get install git`

Mac: `$ brew install git`

Java 7
------
Mac: [Download](https://s3-ap-southeast-2.amazonaws.com/stocksoftware-installers/jdk7/mac/jdk-7u79-macosx-x64.dmg)

Java 8
------
Currently only required for ARENA development.

Rbenv
-----
Mac: `$ brew install rbenv ruby-build`

Ubuntu: `$ git clone` (then add entries to ~/.bashrc)

Ruby 1.9.3
----------
`$ rbenv install 1.9.3-p327` (used by infrastructure)

Ruby 2.1.3
----------
`$ rbenv install 2.1.3` (used by most projects)

jRuby 1.7.2
-----------
`$ rbenv install jruby-1.7.2` (used by dbt)

Intellij Idea
-------------
[Download](https://www.jetbrains.com/idea/download/)
Also need to be allocated a licence.

* Ruby plugin (Jetbrains)
* SwungWeave plugin (repository)

Libre Office
------------

VPN
---
Mac: [Download Cisco AnyConnect mobility client 3.1](https://s3-ap-southeast-2.amazonaws.com/stocksoftware-installers/CiscoAnyConnect/mac/anyconnect-macosx-i386-3.1.06079-k9.dmg)
 
Slack
-----

Source Tree (Mac only)
----------------------

FreeTDS
-------
Mac: `$ brew install freetds` (required to build tiny_tds gem for SQL Server)

Payara
------
Mac: Download, unpack to ~/Applications/payara

Keepass 2.30
------------
[Download](http://keepass.info/download.html) (requires Mono and XQuartz on a Mac)

First Project
=============

`$ gem install bundler`
  
`$ rbenv rehash`

`$ bundle install`

`$ rbenv rehash`