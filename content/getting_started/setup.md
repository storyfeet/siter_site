{{export title="Setup"}}{{@md}}

To get started, install the site generator.  The easiest way to do this if you have rust installed is.

    cargo install siter

Choose a directory to work in:

    siter_gen init

or 

    siter_gen init -f <foldername>

This will create a directory with the following structure

* out\_config.ito (This will be empty but needs to exist)
* content
    * index.md
* templates
    * page.html
* static

if you then run 

    siter_gen -r "out\_config.ito"

The site will be generated into the "public" folder.

