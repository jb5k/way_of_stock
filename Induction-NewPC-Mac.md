# New Computer Checklist

* Create User:
* Install Homebrew: [InstallHomebrew.md](InstallHomebrew.md).
* Install Chrome: `brew cask install google-chrome`.
* Git: See [SetupGit.md](SetupGit.md).
* Java 7: See [InstallJava.md](InstallJava.md).
* Java 8: See [InstallJava.md](InstallJava.md).
* Intellij Idea: See [InstallIntellijIDEA.md](InstallIntellijIDEA.md).
* Ruby: See [InstallRuby.md](InstallRuby.md).
* Buildr: See [InstallGemDependencies.md](InstallGemDependencies.md).
* Payara: See [InstallGlassFish.md](InstallGlassFish.md).
* NodeJS: See [HowToNodeJS.md](HowToNodeJS.md).
* Postgres: See [InstallPostgres.md](InstallPostgres.md).
* LibreOffice: `brew cask install libreoffice`
* VPN: [Download Cisco AnyConnect mobility client 3.1](https://s3-ap-southeast-2.amazonaws.com/stocksoftware-installers/CiscoAnyConnect/mac/anyconnect-macosx-i386-3.1.06079-k9.dmg).
* Keepass: See [InstallKeePass.md](InstallKeePass.md).
* Slack: `brew cask install slack`
* Source Tree: `brew cask install sourcetree`
* Bookmarks: Add all the links on the [External Services](ExternalServices.md) page.

## Set up Localhost (Mac only)

You may run into problems when connecting to the VPN whereby your localhost turns into something
unrecognisable. If this happens issue the following command replacing computer_name with your machines
name e.g. 'Karens-MacBook-Pro':-

```sh
sudo scutil --set HostName <computer_name>.local
```
