# MediaTrix

[Project status: not started]

MediaTrix is a series of multimedia editors wrapped into a programming language.

## Projects

*Main page: [Projects](Projects)*

If you open the GUI version, this will be the first thing you see. Basically, a project is a collection of files. For some reason I am kinda failing to figure out how to explain the logic behind it.

## The language

*Main page: [Language](Language)*

The language itself is based somewhat on Lisp (inspired from GIMP's Script-Fu stuff), only really similar in formatting.

Some examples:

```lisp
(add 1 2) /* Add 1 and 2 */

(set_var abc (add 1 2)) /* Set "abc" to 1 + 2 */

(randint 1 10 seed=7733) /* Demonstration of optional arguments. This form is only required if they're not sequential, like with Python */
```

## GUIs

Each segment will have a dedicated GUI. However, each will also (maybe) come with a TUI (ex. like how some 90s DOS apps are, and also apps like nano)