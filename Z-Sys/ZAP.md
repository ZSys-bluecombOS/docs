# ZAP
NOTE: EXTREMELY INCOMPLETE (and honestly I have no idea what I'm doing)

ZAP (short for Z-Apps) is an attempt at a cross-architecture Assembly-like language, though it is more C-like (in source code form) if you use the higher-level additions.

Source code can be compiled into ZAP's own bytecode format (.zap, as I'm sure you could have guessed). On Z-Sys (official versions, but also hopefully unofficial ports), these can run natively on Z-Sys, like other applications (well, not really, it's still through an emulator-type thing, just in the background so it appears like it's native). Eventually there should be emulators for Windows, macOS, and other OSes, to make it truly cross-platform.

An app for compiling C to ZAP bytecode may be attempted in the future, possibly along with converters for other Assembly forms (like x86 to ZAP).

## Details on official implementations
Pretty much ust emulators.

## Source code commands
### Direct to bytes

| Command | Byte form | Description |
|---|---|---|
| `HALT` | `00` | Stop program (not necessary to written form, but can be used, and in places other than the end of the code) |
| `ADD [var] [var]` | `01` | Add input 1 and input 2 |
| `SUB [var] [var]` | `02` | Subtract input 2 from input 1 |
| `MUL [var] [var]` | `03` | Multiply input 1 and input 2 |
| `DIV [var] [var]` | `04` | Divide input 1 by input 2 |
| `MOD [var] [var]` | `05` | Modulo input 1 by input 2 (remainder in division) |
| `LSH [var] [var]` | `06` | Left shift input 1 (ex. 00001100 --> 00011000) |
| `RSH [var] [var]` | `07` | Right shift input 1 (ex. 00001100 --> 00000110) |
| `LSHL [var] [var]` | `08` | Left shift input 1, with looping (ex. 10000000 --> 00000001) |
| `RSHL [var] [var]` | `09` | Right shift input 1, with looping (ex. 00000011 --> 10000001) |
| `CMP_EQ [var] [var]` | `10` | Check if input 1 and 2 are equal |
| `CMP_LT [var] [var]` | `11` | Check if input 1 is less than input 2 |
| `CMP_GT [var] [var]` | `12` | Check if input 1 is greater than input 2 |
| `JMP [var]` | `13` | Jump to location |
| `JMP_IF [var] [loc]` | `14` | Jump to location if value in given register is true|
| `JMP_IF_NOT [var] [loc]` | `15` | Jump to location if value in given register is false |
| `CALL [var]` | `16` | Call another location, like a function |

### Higher level stuff

| Command | Description |
|---|---|
| `FOR_RANGE ([variable name], [start], [stop], [step]) {...}` | Standard for loop for ranges |
| `FOR_ITEM ([variable name], [list or other iterable]) {...}` | Standard for loop for items in a list |
| `WHILE ([comparison]) {...}` | Standard while loop (comparison will use CMP_xx as you might guess, ex. `WHILE (CMP_EQ [var 1] [var 2]) {...}`) |
| `SET [variable name] [value]` | Set a value (name can't use spaces) (not completely certain of how this one should work yet) |
| `FUNCTION [name](...) {...}` | Standard function. |
| `STRUCT [name](...) {...}` | Ripped straight from C, though with an adjustment: you can set any attribute to be a union of others |
| `CLASS [name](...) {...}` | Similar thing, except now you get fucntions. Pretty much what you'd imagine |

### Other stuff

| Command | Description |
|---|---|
| `ALIAS [original] [new name]` | You can pick a command and a new name that will point to it, like `ALIAS ADD addition` (all caps is not required for the new name). You can also do something like `ALIAS "ADD a b" "a + b"`. Names for inputs go from lowercase A to lowercase Z. This is moreso a compiler detail, so it won't appear in the compiled form. |
| `IGNORE [keyword]` | You can pick words and anything else to ignore, ex. `IGNORE PLEASE`. Case sensitive. |
| `#meta [detail name] "[value]"` | Thing to add metadata like Windows PE and similar things. Spaces are not allowed in the name. Example use: `#meta ProgramName "whatever"`. |
| `#meta DebugInfo "[value]"` | Not really a separate thing, just works a bit different, so thought it should get its own row. This can store variable names, function names, or labels and their locations in the code, based on how the value is set here.<br>"value" can contain any of "f" (to keep function names), "v" (to keep variable names), "l" (to keep label names), "c" (to keep class and struct names). You can include multiple options. Anything that's not these will be ignored, since it will probably just be based on whether each is present. |

### SYS
SYS is the system call one and there is a *lot*, so I gave it its own section

The byte conversions all start with 40, and byte 2 is a category.

| Command | Byte form | Description |
|---|---|---|
| `SYS.IO.PRINT` | `00 00` | Print byte directly |
| `SYS.IO.INPUT` | `00 01` | Text input, like Python's |