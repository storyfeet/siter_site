{{export
title="File Structure"
in_menu=true
order = 2
}}{{@md}}

There are four kinds of files in siter, though three of them are the same type.

* Config Files. (templito)
* Content Files. (templito)
* Template Files. (templito)
* Static files. (Any type)

## Config Files

The root config file can set the locations for look for the other files and where to put the output, it can also define variables that all the other templates can refer to.

An example config file might look like this :

{{/md}}
<pre><code>
\{{export 
output="my_output_path"
content=["content_folder_1","content_folder_2"]
}}
\{{@export menu}}{{@html_esc}}
<a href="/">Home</a>
<a href="/about">About</a>
<a href="/food">Food</a>
<a href="/other">Other</a>
{{/html_esc}}\{{/export}}
</code></pre>

{{@md}}

In the above: "menu" is a made up variable but "output" and "content" are configuration values".

The relevant config varables are:

* output - the folder to write the generated site to. default:"public"
* templates - The locations of the template files. default: ["templates"]
* content  - The locations of the template files. default: ["content"]
* static - The locations of the template files. default: ["static"]
* out\_path - The location the current file will be written to, this is set based on the path to the current file but can be overriden in that file.
* ext - The file extention to attatch to the resulting file.

## The config tree

The root_config item builds a config object. As each content folder is explored it builds it's own config object, this one links to the config object for the folder's parent. This means that if, in any content folder you override a variable in the parent, it is only overridden within that folder.

There are three ways to get information from a config object, this will be the '$0' parameter in any template.

* ```$0.variable_name``` : The lowest/most recent instance of the variable in the tree
* ```$0.lock.variable_name``` : The instance closest to the Root.
    Meaning that even if a variable was overidden, you can still access the original. 
    This is helpful for things like output which shouldn't change halfway through the process.
* ```$0.build.variable_name``` : This builds a path out of all of the instances of that variable.  Absolute paths are considered take over from their parents.


## Order of execution.

* read the root config. 
* For every folder listed in the "content" variable ($f).
    * Look for and try to run a ```($f)/_config.ito``` Building a new config item
    * For every file recursively in ($f) that does not start with '_'
        * Run the template.
        * Find and run the correct template for the templates 'type'
            passing on the config as $0 and the content result as $1
        * Output the contents of the file to the file $out_path
* For every folder listed in the "static" variable.
    * For every file and folder recursively in that 
        *   check the file is newer than that which may be in the target location
        *   write the static file to the target location.


