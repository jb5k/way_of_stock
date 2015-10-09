# Install GlassFish/Payara

The app server of choice is Payara/GlassFish. [Payara Server](http://www.payara.co.uk/) is a drop in replacement for
GlassFish Server with the peace of mind of quarterly releases containing enhancements, bug fixes and patches to
upstream GlassFish Server and dependent libraries including Tyrus, Eclipse Link, Jersey and others. The version of
Payara we currently use is `4.1.152`.

## Download IDEA

The product can be downloaded from [http://www.payara.co.uk/previous_releases](http://www.payara.co.uk/previous_releases).
This should be downloaded and unzipped into the directory `~/Application/payara-4.1.152`.

## Configuring the shell path

The only other action required is to add Payara's components to the path for the shell. The simplest way to do this
is to append the following line to `~/.bashrc`.

    export PATH=$PATH:~/Applications/payara-4.1.152/mq/bin:~/Applications/payara-4.1.152/glassfish/bin
