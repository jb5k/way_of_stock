# Overview

Most projects expect thatjava is installed and the ``JAVA_HOME`` is set to the correct location.

## OSX Instructions

To install under OSX, simply download and run the installer from the Oracle JDK website:

<http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html>

Add the following snippet to `~/.bashrc`;

    export JAVA_HOME=$(/usr/libexec/java_home)

Run `~/.bashrc`;

    $ source ~/.bashrc

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
