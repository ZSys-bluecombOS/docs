# ZAP
ZAP (short for Z-Apps) is an attempt at a cross-architecture Assembly-like language, though it is more C-like (in source code form) if you use the higher-level additions.

Source code can be compiled into ZAP's own bytecode format (.zap, as I'm sure you could have guessed). On Z-Sys (official versions, but also hopefully unofficial ports), these can run natively on Z-Sys, like other applications (well, not really, it's still through an emulator-type thing, just in the background so it appears like it's native). Eventually there should be emulators for Windows, macOS, and other OSes, to make it truly cross-platform.

An app for compiling C to ZAP bytecode may be attempted in the future, possibly along with converters for other Assembly forms (like x86 to ZAP).

## Details on official implementations
They will be written a lot like emulators.

For example, memory will just be a long set of bytes.

Registers are usable in the code, though some mix with some of the higher-level stuff, so unsure if you should really mix them.
List:
* T0-T15 - General-purpose temporaries (64-bit)
* V0-V256 - Variables (yes, like in C and other languages) (these are slots that have 64-bit pointers to data in memory)

## Source code commands
### Direct to bytes

| Command | Byte form | Description | Inputs |
|---|---|---|---|
| `HALT` | `00` | Stop program (not necessary to written form, but can be used, and in places other than the end of the code) | N/A |
| `ADD` | `01` | Add input 1 and input 2 (x + y) | 2 registers |
| `SUB` | `02` | Subtract input 2 from input 1 (x - y) | 2 registers |
| `MUL` | `03` | Multiply input 1 and input 2 | 2 registers |
| `DIV` | `04` | Divide input 1 by input 2 | 2 registers |
| `MOD` | `05` | Modulo input 1 by input 2 (remainder in division) | 2 registers |
| `LSH` | `06` | Left shift input 1 (ex. 00001100 --> 00011000) | 1 register |
| `RSH` | `07` | Right shift input 1 (ex. 00001100 --> 00000110) | 1 register |
| `CMP_EQ` | `10` | Check if 2 values are equal | 2 registers |

### Higher level stuff

| Command | Description |
|---|---|
| `FOR_RANGE ([variable name], [start], [stop], [step]) {...}` | Standard for loop for ranges |
| `FOR_ITEM ([variable name], [list or other iterable]) {...}` | Standard for loop for items in a list |
| `WHILE ([comparison]) {...}` | Standard while loop (comparison will use CMP_xx as you might guess, ex. `WHILE (CMP_EQ [var 1] [var 2]) {...}` |
| `SET [variable name] [value]` | Set a value (name can't use spaces) (not completely certain of how this one should work yet) |

### Other stuff

| Command | Description |
|---|---|
| `ALIAS [original] [new name]` | You can pick a command and a new name that will point to it, like `ALIAS ADD addition` (all caps is not required for the new name). This is moreso a compiler detail, so it won't appear in the compiled form. |
| `#meta [detail name] "[value]"` | Thing to add metadata like Windows PE and similar things. Spaces are not allowed in the name. Example use: `#meta ProgramName "whatever"`. |
| `#meta DebugInfo "[value]"` | Not really a separate thing, just works a bit different, so thought it should get its own row. This can store variable names, function names, or labels and their locations in the code, based on how the value is set here.<br>"value" can contain any of "f" (to keep function names), "v" (to keep variable names), or "l" (to keep label names). You can include multiple options. Anything that's not these will be ignored, since it will probably just be based on whether each is present. |

### SYS
SYS is the system call one and there is a *lot*, so I gave it its own section
The byte conversions all start with 40

| Command | Byte form | Description |
|---|---|---|
| `SYS.IO.PRINT` | `00 00` | Print byte directly |
| `SYS.IO.PRINTNUM` | `00 01` | Print decimal value of byte |
| `SYS.IO.PRINTHEX` | `00 02` | Print hexadecimal value of byte |
