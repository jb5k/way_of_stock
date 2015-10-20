# New Computer Checklist

* Create User: Goto "Settings | User Accounts"
* Install Chrome: [Download](http://www.google.com/chrome/).  Save to disk and open with Software Centre.
* Git: See [SetupGit.md](SetupGit.md).
* Java 7: See [InstallJava.md](InstallJava.md).
* Java 8: See [InstallJava.md](InstallJava.md).
* Intellij Idea: See [InstallIntellijIDEA.md](InstallIntellijIDEA.md).
* Ruby: See [InstallRuby.md](InstallRuby.md).
* Buildr: See [InstallGemDependencies.md](InstallGemDependencies.md).
* Payara: See [InstallGlassFish.md](InstallGlassFish.md).
* NodeJS: See [HowToNodeJS.md](HowToNodeJS.md).
* Postgres: See [InstallPostgres.md](InstallPostgres.md).
* LibreOffice: Already installed by default.
* VPN: Use Ubuntu built-in VPN client.
* Keepass: See [InstallKeePass.md](InstallKeePass.md).
* Bookmarks: Add [Slack](http://todo)

## VPN Issues

To ensure the DNS behaves correctly when connected to the FEM VPN, you are forced to disable DNSMasq. To do this
you edit network configuration via:

    $ gksu gedit /etc/NetworkManager/NetworkManager.conf

And comment out dnsmasq so that it looks like:

    #dns=dnsmasq

And restart the network manager via:

    $ sudo service network-manager restart
