# MtxColor

A little class for colors.

All of the class methods revolve around converting between color types. However, there is one thing of note: values that don't loop (e.g. HSV Hue) are uncapped.

The GUI is a color picker, basically, and will likely be used as one for other editors.

Also, the class itself will be used as the basis for all things related to color in the other editors. The uncapped format is helpful for the other editors, I believe.