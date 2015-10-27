# Overview

We use `rbenv`, a ruby version manager, to manage the ruby versions used by each project. To install
ruby we first install `rbenv` then issue commands to rbenv to install the correct versions of ruby.

Ruby and `rbenv` are required by a project when there exists a file named `.ruby-version` in the base
directory of the project.

## Installing rbenv

### OSX Instructions

Under OSX with [Homebrew](InstallHomebrew.md) installed you can install via;

    $ brew update
    $ brew install rbenv
    $ brew install ruby-build

### Linux Instructions

Under Linux you need to checkout rbenv from Git;

    $ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
    $ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

Add the following snippet to `~/.bashrc`;

    PATH=$PATH:$HOME/.rbenv/bin
    eval "$(rbenv init -)"

Run `~/.bashrc`;

    $ source ~/.bashrc

## Installing ruby

Most projects use the _2.1.3_ version of ruby. The version of ruby used by a project can be determined by
reading the contents of the `.ruby-version` in the base directory of the project. Replace _2.1.3_ in the
following instructions with the version that the project actually uses.

Under Linux, first install required dependencies:

    $ sudo apt-get install -y libxml2-dev libssl-dev libreadline-dev zlib1g-dev

To install ruby, it is as simple as:

    $ rbenv install 2.1.3

Note that if the 2.1.3 version is not listed when you do:

    $ rbenv install --list

Then under OSX you may need to do a:

    $ brew upgrade ruby-build

While under Linux you may need to do:

    $ cd ~/.rbenv/plugins/ruby-build
    $ git pull

Projects that use dbt to manage the database automation also require the presence of a specific version of
jruby. This is a bug/limitation of dbt and may be fixed at some future point but until such a time, the jruby
version can be installed by:

    $ rbenv install jruby-1.7.2

Under Linux you _may_ need to install the dependency:

    $ sudo apt-get install -y g++
