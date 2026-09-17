# MtxColor

A little class for colors.

All of the class methods revolve around converting between color types. However, there is one thing of note: values that don't loop (e.g. HSV Hue loops, R/G/B don't) are uncapped.

The GUI is a color picker, basically, and will likely be used as one for other editors.

Also, the class itself will be used as the basis for all things related to color in the other editors (ex. as pixels, or colors of things). The uncapped format is helpful for the other editors, I believe.

All color type classes are subclasses of the main MtxColor class. Custom ones should be possible by including conversions to other color formats.



Additional things in this section, at this time, include a method for converting RGB hex codes to RGB class.