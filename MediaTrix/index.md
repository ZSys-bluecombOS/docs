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

The language itself is based somewhat on Lisp (inspired from GIMP's Script-Fu in particular), but only really similar in formatting, as I did also make it from scratch.

Some examples:

```lisp
(add 1 2) /* Add 1 and 2 */

(set_var abc (add 1 2)) /* Set "abc" to 1 + 2 */

(randint 1 10 seed=7733) /* Demonstration of optional arguments. This form is only required if they're not sequential, like with Python */
```

You can use the multimedia editors from inside the language itself, somewhat similarly to Python's PIL/Pillow, for example

## The editors

To note: many of these don't really have anything special, the goal is moreso to match the rest in capability.
* [MtxColor](MtxColor) - converter between different color types, used for `MtxImage` because the values don't have to be capped (except for ones that loop, like HSL Hue) (GUI will be color picker, although more elaborate probably because of the extra color modes instead of only working in RGB)
* [MtxBytes](MtxBytes) - actually just bytes, like Python's `bytearray` (GUI will be a hex editor, but with extra stuff)
* [MtxMath](MtxMath) - Calculator kinda (you can put equations in and then evaluate them with certain values for each variable) (GUI version, at least, may be similar to Desmos graphing calculator)
* [MtxGUI](MtxGUI) - A basic GUI creator thing (GUI version probably won't be based on anything, but as for details, it will be drag and drop) - also plan to have this be capable of automatically creating TUI and HTML versions of the layout
* ---
* [MtxImage](MtxImage) - Image editor (like GIMP)
* [MtxVector](MtxVector) - Vector image editor (like Inkscape)
* [MtxFont](MtxFont) - Font editor (like FontStruct) (pixel fonts may be here also, or I may make a separate one)
* [MtxVideo](MtxVideo) - Video editor (like VSDC)
* [MtxCaps](MtxCaps) - Subtitle editor (I have no examples for this unfortunately)
* [MtxAudio](MtxAudio) - Audio editor (like Audacity)
* [MtxMIDI](MtxMIDI) - MIDI editor kind of thing (like some part of FL Studio) (the MediaTrix equivalent of Vocaloid/Utau or whatever will probably be through this since it has the notes form) (also, `MtxMIDI` name may be changed in the future if I come up with something better)
* [Mtx3D](Mtx3D) - 3D editor (like Blender)
* ---
* [MtxDocument](MtxDocument) - Document editor (like MS Word)
* [MtxPresent](MtxPresent) - Presentation editor (like MS PowerPoint)
* [MtxSheet](MtxSheet) - Spreadsheet editor (like MS Excel)
* ---
* [MtxGame](MtxGame) - Game engine type of thing (like Unity?) (2D and 3D may be merged together)
* ---
* [MtxAI](MtxAI) - Local AI app and editor (like Unsloth Studio I think)
* [MtxHost](MtxHost) - A way to locally host stuff like webpages (like nginx but only to some extent, because it can be used to locally host things like AI models or whole MtxProjects)

## GUIs

Each segment will have a dedicated GUI. They will be made in MtxGUI for convenience.

## `mtxout`

*Full documentation: [mtxout](mtxout)*

MediaTrix Output (`.mtxout`) is a specialized XML-like format for storing bundles of files. Primarily, this is used for exporting Projects. However, this is also the format used to save any sort of MediaTrix files (like layer files for image editors, essentially, but used for all formats).