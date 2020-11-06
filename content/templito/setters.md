{{export
    title = "Setters"
    in_menu = true
    order = 0
}}{{@md}}

## Local Variables.

To set a variable, use "let"

    \{{let a = 3}}There are \{{$a}} cats

will output

    There are 3 cats

If you want to make the function that called the template aware of the variable use export

## Exported Variables

{{export title="This Title", order=3}}

In the context of Siter, this will mean that these variables are available at the next stage of templating.  If you export a variable in the "Content" file it will be available to the "Page" file.

Simple Value exports, (those not dependent on running another template, which is most of them) are also added to the result of the "scan_dir" function (more later), so you can refer to them in menus etc.

## Block Setters

The '@' sigil allows us to set a value to the result of running a block.

    \{{@let car}}Rover\{{/let}}My car is a \{{$car}}.

Will output 

    My car is a Rover.

This is generally more useful when you want to include Conditional blocks in the output, or when exporting complex strings.

    \{{let bg = "#454545"}}
    \{{@export css}}\\
    .ident{
        background:\{{$bg}};
    }
    \{{/export}}



