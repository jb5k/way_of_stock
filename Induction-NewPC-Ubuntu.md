New Computer Checklist
======================

Create User
-----------
Settings | User Accounts

Chrome
------
[Download](http://www.google.com/chrome/).  Save to disk and open with Software Centre.

Git
---
Use Software Centre.

Java 7
------
See [InstallJava.md](InstallJava.md).

Java 8
------
See [InstallJava.md](InstallJava.md), except use:

    $ sudo apt-get install oracle-java8-installer

Currently only required for ARENA development.

Intellij Idea
-------------
See [InstallIntellijIDEA.md](InstallIntellijIDEA.md).

Ruby
----

See [InstallRuby.md](InstallRuby.md).

Buildr
------
See [InstallGemDependencies.md](InstallGemDependencies.md).

Payara
------
See [InstallGlassFish.md](InstallGlassFish.md).

NodeJS
------
See [HowToNodeJS.md](HowToNodeJS.md).

Postgres DB
-----------
Install the vanilla server:

    $ sudo apt-get install postgresql postgresql-contrib

OR: install the server with postgis enabled:

    $ sudo apt-get install postgresql-9.3-postgis-2.1

Create a user that will be used to interact with the database:

    $ sudo -u postgres psql postgres
    $ CREATE ROLE "stock-dev" WITH PASSWORD 'letmein' CREATEDB SUPERUSER LOGIN;

Install the client "pgAdmin III" from the Software Centre.

LibreOffice
------------
Already installed by default.

VPN
---
Use Ubuntu built-in VPN client.

Keepass 2.30
------------
[Download](http://keepass.info/download.html)

Bookmarks
---------
[Slack](http://todo)
