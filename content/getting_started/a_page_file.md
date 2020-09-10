{{export
title = "A Page File"
in_menu = true
order = 3
}}{{@md}}

The job of the page files is to take the result of a content file and make it into a complete html webpage.  These are stored in the "templates" folder.

The main page file for this website "templates/page.html" looks **exactly** like this.

There are several fancy tricks in this file, so I will break them down below
{{/md}}
<pre><code>
{{html_esc (file "templates/page.html")}}
</code></pre>
{{@md}}

### Export as_index = true

Tells the system to create a folder instead of a file at the location and output the result to "folder/index.html"

### Backslaches before whitespace

Ignore all white space up to the next non-whitespace character, if that is also a backslash ignore it too.

### First

    \{{first .title "Siter - Site Generator"}}

The special function "first" will choose the first valid parameter. This function evaluates lazily and will return the first result considered valid.  If none of them do it will return "null"

So using ```{{first .title "Default Title"}}``` allows us to provide a convenient default.

```.title``` is short hand for ```$0.title``` . More below.

### Menu generation.

    \{{ .menu}}

If we want to auto generate a menu, we can, by taking advantage of the "scan_dir" function. 

But generating the menu for every page will mean rescanning all the files for the same info every time.

To do the generation only once, we do it in a config file, and export it as a string variable. (in this case called menu).

Then all content files can refer to it, without needing to regenerate it.

### Breadcrumbs

A clickable path from '/' to the current page.

```
\{{let bp = bread_crumbs .build.out_path}}
\{{let blen = len $bp }}
<a href="/">Home</a> 
\{{if gt $blen 2}}
	\{{for k v in slice $bp 1 (sub $blen 1) }}
	/ <a href="/\{{$v}}">\{{base_name_sure $v}}</a>
	\{{/for}}
\{{/if}}

```

1. ```.build.out_path``` will grab gets the output path for this file from the config.
2. ```breadcrumbs``` takes the path and turns it into a list of paths to each part.
3. store that in ```$bp```
4. If the length of breadcrumbs is less than 2 then it's only "Home" and the current file, We have nothing to include.
5. ```slice``` to drop the 2 ends off the breadcrumbs.
6. ```for k v in ...``` Loop through the remaining list setting 'k' as the index and 'v' as the value.
7. Build an href. $v is the full target path, ```basename $v``` drops the path, leaving just the filename.



### $1 -- The 1th parameter.

    \{{$1}}

Any templito template can recieve as many paramaters as you like. 
They are accessed using "$n" where "n" is the parameter position.

The first paramater is "$0" however if you want to access a property of "$0" normally you can use the short hand ```.item``` which is exactly the same as writing ```$0.item``` .

To page templates, $0 is the content-file data including it's path, and $1 is it's resolved contents as a string.



