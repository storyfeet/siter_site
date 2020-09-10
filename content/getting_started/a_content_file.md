{{#Start with the exports, you can make up your own if you like#}}
{{export
title = "A Content File"
in_menu = true
order = 2
}}\
{{#The next section will be treated as markdown , '@' makes any function work on the result of the block it starts#}}
{{@md}}

Content files in Siter are written using the same templating language as the formatting templates.  This has some significant advantages for being able to tweak the content of specific pages as needed.

Take this file for example.  Because it is a template, I am able to include it inside itself.

Not something you want to do that often I suppose but having the flexibility to do this can be helpful.

Template magic is always wrapped in ```\{{}}``` and comments are wrapped in ```\{{#  #}}``` 

{{# End the markdown so we can work with actual html #}}
{{/md}}
<pre><code>
{{#load the file and make it html safe #}}
{{html_esc (file "content/getting_started/a_content_file.md")}}
</code></pre>

{{@md}}

As you can see this contains a few fany tricks

