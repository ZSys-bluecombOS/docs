# ZAP
ZAP (short for Z-Apps) is an attempt at a cross-architecture Assembly-like language, though it is more C-like (in source code form) if you use the higher-level additions.

Source code can be compiled into ZAP's own bytecode format (.zap, as I'm sure you could have guessed). On Z-Sys (official versions, but also hopefully unofficial ports), these can run natively on Z-Sys, like other applications (well, not really, it's still through an emulator-type thing, just in the background so it appears like it's native). Eventually there should be emulators for Windows, macOS, and other OSes, to make it truly cross-platform.

An app for compiling C to ZAP bytecode may be attempted in the future, possibly along with converters for other Assembly forms (like x86 to ZAP).

## Details on official implementations
They will be written a lot like emulators.

For example, memory will just be a long set of bytes.

Registers:
* T00-T15 - General-purpose temporaries

## Source code commands
### Direct to bytes
| Command | Byte form | Description | Inputs |
|---|---|---|---|
| `HALT` | `00` | Stop program (not necessary to written form) | N/A |
| `ADD` | `01` | Add input 1 and input 2 (x + y) | 2 registers |
| `SUB` | `02` | Subtract input 2 from input 1 (x - y) | 2 registers |
| `MUL` | `03` | Multiply input 1 and input 2 | 2 registers |
| `DIV` | `04` | Divide input 1 by input 2 | 2 registers |
### Other
| Command | Description |
|---|---|
| `ALIAS [original] [new name]` | You can pick a command and a new name that will point to it, like `ALIAS ADD addition` (all caps is not required for the new name). This is moreso a compiler detail, so it won't appear in the compiled form. |
