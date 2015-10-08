# Install Pg

Pg is the native library used to talk to Postgres database. It is only required if the project
talks to Postgres. It is primarily used by the `pg` gem dependency.

## OSX Instructions

Under OSX with [Homebrew](http://mxcl.github.com/homebrew/) installed you can install via;

    $ brew update
    $ brew install postgresql

Note that this installs the full database. The client libraries are included with the database.

## Linux Instructions

To install under linux we install the package via;

    $ sudo apt-get install libpq-dev
