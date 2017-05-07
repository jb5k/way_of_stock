# NodeJS

NodeJS is a javascript environment for the server and command line. We primarily use it to run
tooling. We use `nvm` a node version manager, to manage the node versions used by each project.
To install node we first install `nvm` then issue commands to rbenv to install the correct versions
of node.

Node and `nvm` are required by a project when there exists a file named `.nvmrc` in the base
directory of the project.

## Installing nvm

### OSX Instructions

Under OSX with [Homebrew](Homebrew.md) installed you can install via;

    $ brew update
    $ brew install nvm

## Installing NodeJS

Most projects use _v6.10.3_, the latest LTS version of node. The version of node used by a project can be
determined by reading the contents of the `.nvmrc` in the base directory of the project. Replace _v6.10.3_
in the following instructions with the version that the project actually uses.

To install ruby, it is as simple as:

    $ nvm install v6.10.3

## Using Node Package Manager

[NPM] (from https://npmjs.org/) or the Node Package Manager is the standard mechanism for installing
tools and libraries in the Node ecosystem. Node packages can either be installed globally or locally
to the project. As all of our projects use a limited subset of tools we tend to install globally which
means passing the `-g` flag to `npm`.

An example of how to install Less.js a CSS preprocessor that we have used is:

    $ sudo npm install -g less
    $ sudo npm install -g less-plugin-clean-css
