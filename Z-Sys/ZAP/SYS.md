# ZAP SYS calls
SYS is the system call one and there is a *lot*, so I gave it its own page

The byte conversions all start with 40, and byte 2 is generally a category.

| Command | Byte form | Description |
|---|---|---|
| `SYS.IO.PRINT` | `00 00` | Print byte directly |
| `SYS.IO.INPUT` | `00 01` | Text input, like Python's |