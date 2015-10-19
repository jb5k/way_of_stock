# Way of Stock Software

The purpose of this repository is to document the standard tools and processes that are used
in Stock Software's projects. It is neither complete nor set in stone and it is expected to
evolve and be refined over time.

## Basic Host Setup

Before starting any project, please ensure that your shell is correctly setup.

* [Install Homebrew](InstallHomebrew.md) (Mac Only)
* [Setup git](SetupGit.md)
* [Setting up the shell prompt](SetupShellPrompt.md)

## Environment Setup

The following documents describe environment setup for our projects. Not all projects use all of these
features but they likely to be required by many projects.

* [Install ruby and rbenv](InstallRuby.md)
* [Install java](InstallJava.md)
* [Install freetds library](InstallFreeTDS.md)
* [Install gem dependencies](InstallGemDependencies.md)
* [Install IntelliJ IDEA](InstallIntellijIDEA.md)
* [Install GlassFish](InstallGlassFish.md)
* [Install Docker](InstallDocker.md)

## Essential Tools

The following documents describe some of the essential tools in use in our projects. They should give a starting
point for using the tools within the context of our projects.

* [Braid](HowToBraid.md): Vendor branch management tool.
* [Buildr](HowToBuildr.md): Build automation tool.
* [NodeJS](HowToNodeJS.md): Javascript runtime environment and ecosystem.
* [QBroswerLite](QBrowserLite.md): OpenMQ Message Broker Destination browser.
* [KeePass](KeePass.md): Password locker where shared passwords and credentials are stored.
* [Postgres](InstallPostgres.md): Postgres database server.

## Learning Goals

Most people should be able to perform the basic tasks required by our projects. To start to promote this
we are trying to develop a series of checklists to document what you should be able to do:

* [Learning Checklist](LearningChecklist.md)
