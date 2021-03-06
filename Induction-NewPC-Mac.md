# New Computer Checklist

* Create User:
* Install Homebrew: [Homebrew.md](Homebrew.md).
* Install Chrome:
* Git: See [Git.md](Git.md).
* Java 7: See [Java.md](Java.md).
* Java 8: See [Java.md](Java.md).
* Intellij Idea: See [IntellijIDEA.md](IntellijIDEA.md).
* Ruby: See [Ruby.md](Ruby.md).
* Buildr: See [GemDependencies.md](GemDependencies.md).
* Payara: See [GlassFish.md](GlassFish.md).
* NodeJS: See [HowToNodeJS.md](NodeJS.md).
* Postgres: See [Postgres.md](Postgres.md).
* LibreOffice:
* VPN: Go to https://vpn.ffm.vic.gov.au log in and download/install the Mac client
* Keepass: See [KeePass.md](KeePass.md).
* Source Tree:
* Bookmarks: Add all the links on the [External Services](ExternalServices.md) page.

## Set up Localhost (Mac only)

You may run into problems when connecting to the VPN whereby your localhost turns into something
unrecognisable. If this happens issue the following command replacing computer_name with your machines
name e.g. 'Karens-MacBook-Pro':-

```sh
sudo scutil --set HostName <computer_name>.local
```
