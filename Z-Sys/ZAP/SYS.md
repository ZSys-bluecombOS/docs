# ZAP SYS calls
SYS is the system call one and there is a *lot*, so I gave it its own page

The byte conversions all start with 40, and byte 2 is generally a category.

| Command | Byte form | Description |
|---|---|---|
| `SYS.IO.PRINT [var]` | `00 00` | Print text |
| `SYS.IO.INPUT [text]` | `00 01` | Text input, like Python's |