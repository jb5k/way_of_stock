# Setup Git

## Install Git

Git is likely already installed but if not, it will need to be installed.

### OSX Instructions

Under OSX with [Homebrew](http://mxcl.github.com/homebrew/) installed you can install via;

    $ brew update
    $ brew install git

### Linux Instructions

To install under linux we install the package via;

    $ sudo apt-get install git

## Configuring Basic Settings

The first thing you should do when you install Git is to set your user name and email address. This is important
because every Git commit uses this information, and it’s immutably baked into the commits you start creating:

    $ git config --global user.name "My Name"
    $ git config --global user.email myname@example.com

Again, you need to do this only once if you pass the `--global` option, because then Git will always use that
information for anything you do on that system. If you want to override this with a different name or email
address for specific projects, you can run the command without the `--global` option when you’re in that project.

If the email used in a commit matches a verified GitHub or GitHub Enterprise user account, the account's username
is used on website, instead of the username set by Git.

## Turning off the "helpful" popup when using git gui

When running `git gui` you will almost always get a warning that there is too many loose objects and a gc
is required. This message can be disabled by running the following command:

    $ git config --global gui.gcwarning false

## Setting up Git Global Ignores

Each OS has a separate set of temporary files it will place in each directory. Rather than adding
ignores for all these files into every project, it is easier to set it up at a global level. A
file named `.gitignore_global` should be placed in your home directory with the contents:

    .DS_Store
    .DS_Store?
    ._*
    .Spotlight-V100
    .Trashes
    ehthumbs.db
    Thumbs.db
    *~

Then the following command should be run:

    $ git config --global core.excludesfile ~/.gitignore_global