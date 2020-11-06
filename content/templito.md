{{export
title="The Templito Language"
in_menu=true
}}{{@md}}

Siter is build upon the templito templating language, which is a powerful templating language, similar to "Go Templates" or "Handlebars".  It's two distinguishing features are "Multiple parameters", and "blocks as parameters", we will come to these later.

It is maintained by me, Matthew Stoodley, at 

* [github.com/storyfeet/templito](https://github.com/storyfeet/templito) for Templito
* [github.com/storyfeet/siter](https://github.com/storyfeet/siter) for Siter

If there is a functionality you would like to see, please either raise an issue, make a PR, or email <matt.storyfeet@gmail.com> 

## Plain Text

The purpose of a templito template is to run once, and output plain text, therefor, this is it's focus.
Everything not inside a squigly brace pair ```\{{..}}``` is considered plain text. And will be passed to the result directly.

In plain text string can be escaped using ```\\``` eg:

    \\n:Newline
    \\t:Tab
    \\\{{:\{{
    \\\\:\\

A single squigly brace does not need escaping, (That would make writing css awkward.)

Whitespace (even newlines) can also be escaped eg:

    "\\      hello" : "hello"
    "\\    \\  hello" : "  hello"

## Blocks

There are several kinds of blocks that Templito Understands.  The following pages will go into more detail.

* Comment,    
    Basically ignored
* Pipe(Pipeline),    
    Expressions and function calls
* Block    
    performs an action on the result of a block
* If / Then / Else    
    Conditionally evaluate blocks
* For     
    Evaluates blocks several times with different values
* Define(String, Block),    
    Creates a template and stores it in a variable
* Let(Vec<(String, Pipeline)>),    
    Sets Variable values.
* Export(Vec<(String, Pipeline)>),    
    Sets variables that can be read by the caller of the template.
* AtLet(String, Block),    
    Sets a variable to the result of running a block 
* AtExport(String, Block),    
    Exports the result of running a block.
