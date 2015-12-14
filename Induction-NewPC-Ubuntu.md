# New Computer Checklist

* Create User: Goto "Settings | User Accounts"
* Install Chrome: [Download](http://www.google.com/chrome/).  Save to disk and open with Software Centre.
* Git: See [SetupGit.md](Git.md).
* Java 7: See [InstallJava.md](Java.md).
* Java 8: See [InstallJava.md](Java.md).
* Intellij Idea: See [InstallIntellijIDEA.md](IntellijIDEA.md).
* Ruby: See [InstallRuby.md](Ruby.md).
* Buildr: See [InstallGemDependencies.md](GemDependencies.md).
* Payara: See [InstallGlassFish.md](GlassFish.md).
* NodeJS: See [HowToNodeJS.md](NodeJS.md).
* Postgres: See [InstallPostgres.md](Postgres.md).
* LibreOffice: Already installed by default.
* VPN: Use Ubuntu built-in VPN client.
* Keepass: See [InstallKeePass.md](KeePass.md).
* Bookmarks: Add all the links on the [External Services](ExternalServices.md) page.
* Printer: Add Ricoh-Aficio-MP-C4500 on 10.192.237.102.

## Setting up the DELWP VPN

Install the openconnect network manager

    $ sudo apt-get install network-manager-openconnect-gnome

Add a VPN

     Connection Name: FEM
     Gateway: vpn.fem.vic.gov.au
     Username/Pwd: your fireweb details

## VPN Issues

To ensure the DNS behaves correctly when connected to the FEM VPN, you are forced to disable DNSMasq. To do this
first install gksu:

    $ sudo apt-get install gksu

Then edit network configuration via:

    $ sudo gksu gedit /etc/NetworkManager/NetworkManager.conf

And comment out dnsmasq so that it looks like:

    #dns=dnsmasq

You also need to update the search path for DNS if you want to use short names. Do this by
editing the configuration:

    $ sudo vi /etc/resolvconf/resolv.conf.d/tail

So that it looks like:

    search fem.vic.gov.au femnp.vic.gov.au nre.vic.gov.au fire.dse.vic.gov.au dse.vic.gov.au internal.vic.gov.au

Finally, restart the network manager via:

    $ sudo service network-manager restart
