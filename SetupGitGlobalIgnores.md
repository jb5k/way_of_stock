# Setting up Git Global Ignores

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
