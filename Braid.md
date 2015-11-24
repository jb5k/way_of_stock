# Braid

[Braid](http://cristibalan.github.io/braid/) is a simple tool to help track vendor branches in a
[Git](http://git-scm.com/) repository. That costs and benefits of vendoring in an external library
rather than referencing an external library is well documented on the [Braid](http://cristibalan.github.io/braid/)
website. We use it to vendor in external repositories such as dbt, domgen, rptman as well as documentation
repositories like this repository. A project uses braid if it has a file named `.braids` in the root directory.

For an existing project you can braid in a new project with a command similar to:

    $ braid add https://github.com/stocksoftware/way_of_stock.git vendor/docs/way_of_stock

To update a repository that is already braided in use:

    $ braid update vendor/docs/way_of_stock

Local changes can be made as usual to the braided in repository but when you want to push changes back to
the source directory the typical process is:

    $ braid diff vendor/docs/way_of_stock > ../path/to/way_of_stock/patch.diff
    $ cd ../path/to/way_of_stock
    $ git apply patch.diff
    $ git add .
    $ git commit -m "Added wonderful stuff"
    $ git push

After you have committed and pushed the changes to the source directory it is simply a matter of issuing another
`braid update` command to update the braid. It is recommended that this is done immediately to avoid merge problems
down the track.
