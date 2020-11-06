{{export
title="Templito Functions"
in_menu=true
}}{{@md}}

## rand 

* get_rand

## svg
* xy
* xywh
* xy12
* fl_stk
* xml_esc
* font
}
## maps
* map

## format

For converting strings in these formats into useable data

* r_json (string) - Json file format
* r_card (string) - Card format //TODO LINK

## lists
* list (items ...)- Build a list from the parameters given
* sort (list) - returns a sorted list (Copying data)
* append (list ...)- Append multiple lists into one list (Copying data)
* sort_on (list key) - returns a sorted list on the given key
* bin_search (list key comparator ...) - returns the location of an item in the list, (Comparators should match those the list was sorted on)
* bin_get (list key comparator ...) - returns the item found
* get (list key) - item in list at key
* filter (list string) returns a new list with only the elements that pass the filter. The filter is a boolean expression operating on $0 written as a string)
* len (list) - The length of a list or map
* slice (list start finish) - Slices the list returns a copy of the section
* groups (list group_size) - Splits the list into multiple lists of maximum size group_size.



## strings
* cat
* md
* table
* split
* str_contains
* str_replace
* str_replace_n
* html_esc
* regex
* word_wrap


## math
* add
* sub
* mul
* div
* mod


## bools
* eq
* neq
* eq_any
* gt
* gte
* lt
* lte
* and
* nand
* or
* nor

## files/paths
* parent
* join
* bread_crumbs
* base_name
* base_name_sure
* with_ext
* stem
* full_stem


## folder_lock (Folder)

Read Data from within a specific folder, for Siter, this is the root directory of the project. But can be set to any specific in templito. If the template tries to read out of the folder for example using "../" these will fail.

* dir
* file
* is_file
* is_dir
* scan_dir


## Exec 

Because these functions are not safe to allow non privilidged users access to they are not turned included in the defaults.
Siter currently includes them, as they can be handy, but they my be feature or flag locked at some point.

* exec
* exec_stdin


## write_lock (Folder)

For writing data within a specific folder. In Siter this is the output directory and paths should be given relative to that.

* write

