# MediaTrix

[Project status: not started]

MediaTrix is a series of multimedia editors wrapped into a programming language.

## Various details that are present across all forms

* You get compiler options for all of them, though you also have to make those yourself (for instance, you could set up something so maybe there's some hue shift if you do "-aaa") (I have not thought this through enough to have specific details)

## Projects

*Full documentation: [Projects](Projects)*

If you open the GUI version, this will be the first thing you see. Basically, a project is a bundle of files. It's useful because it makes it easier to work with other files, I think. Or will keep them synced better.

## The language

*Full documentation: [Language](Language)*

The language itself is based somewhat on Lisp (inspired from GIMP's Script-Fu stuff), but only really similar in formatting, as I did also make it from scratch.

Some examples:

```lisp
(add 1 2) /* Add 1 and 2 */

(set_var abc (add 1 2)) /* Set "abc" to 1 + 2 */

(randint 1 10 seed=7733) /* Demonstration of optional arguments. This form is only required if they're not sequential, like with Python */
```

You can use the multimedia editors from inside the language itself, somewhat similarly to Python's PIL/Pillow, for example

## GUIs

Each segment will have a dedicated GUI. However, each will also (maybe) come with a TUI (ex. like how some 90s DOS apps are, and also apps like nano) for things stuck in text mode (it does assume support for ANSI)