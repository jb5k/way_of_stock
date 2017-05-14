# NodeJS

NodeJS is a javascript environment for the server and command line. We primarily use it to run
tooling. We use [`nodenv`](https://github.com/nodenv/nodenv) a node version manager, to manage the
node versions used by each project.

To install node we first install `nodenv` then issue commands to `nodenv` to install the correct
versions of node.

Node and `nodenv` are required by a project when there exists a file named `.node-version` in the
base directory of the project.

## Installing nodenv

### OSX Instructions

Under OSX with [Homebrew](Homebrew.md) installed you can install via;

    $ brew update
    $ brew install nodenv

### Linux Instructions

Under Linux you need to run;

    $ git clone https://github.com/nodenv/nodenv.git ~/.nodenv

Optionally, try to compile dynamic bash extension to speed up `nodenv`. Don't worry if it fails; `nodenv`
will still work normally:

    $ cd ~/.nodenv && src/configure && make -C src

Add `~/.nodenv/bin` to your `$PATH` for access to the `nodenv` command-line utility.

    $ echo 'export PATH="$HOME/.nodenv/bin:$PATH"' >> ~/.bashrc

## Installing NodeJS

Most projects use _v6.10.3_, the latest LTS version of node. The version of node used by a project can be
determined by reading the contents of the `.node-version` in the base directory of the project. Replace
_v6.10.3_ in the following instructions with the version that the project actually uses.

To install node, it is as simple as:

    $ nodenv install 6.10.3

## Using Node Package Manager

[NPM] (from https://npmjs.org/) or the Node Package Manager is the standard mechanism for installing
tools and libraries in the Node ecosystem. Node packages can either be installed globally or locally
to the project. As all of our projects use a limited subset of tools we tend to install globally which
means passing the `-g` flag to `npm`.

An example of how to install Less.js a CSS preprocessor that we have used is:

    $ sudo npm install -g less
    $ sudo npm install -g less-plugin-clean-css
    $ nodenv rehash
