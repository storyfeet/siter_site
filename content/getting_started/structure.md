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

The other relevant config varables are:


