# Install Java

Most projects expect that java is installed and the ``JAVA_HOME`` is set to the correct location.

## OSX Instructions

To install under OSX, simply download and run the installer from the Oracle JDK website:

<http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html>

Add the following snippet to `~/.bashrc`;

    export JAVA_HOME=$(/usr/libexec/java_home)

Run `~/.bashrc`;

    $ source ~/.bashrc

Unfortunately due to the way some java programs interact with OSX, they also require that the legacy Java 6
to be present even if it is not used. To install the Java6 JVM the package should be downloaded and installed
from `https://support.apple.com/kb/DL1572?locale=en_US`

## Linux Instructions

To install under linux we install the package from a custom repository;

    $ sudo apt-get install python-software-properties
    $ sudo add-apt-repository ppa:webupd8team/java
    $ sudo apt-get update
    $ sudo apt-get install oracle-java7-installer

Add the following snippet to `~/.bashrc`;

    export JAVA_HOME=/usr/lib/jvm/java-7-oracle

Run `~/.bashrc`;

    $ source ~/.bashrc
