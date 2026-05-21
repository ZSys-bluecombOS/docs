# Super Emulator

[Project status: not started]

Super Emulator is supposed to be a general-purpose, as accurate as possible, "will cover just about anything" kind of emulator.

## Inspiration

I believe this project's existence was mostly based on MAME, because I remember not really understanding how to use it. That was a long time ago though.

As of now, it's mostly the thought of there being things that don't have emulators (ex. Intel Itanium stuff), or inaccurate emulators (ex. Famicom, I guess? since I remember that one ACE thing that doesn't work in emulator, or at least doesn't work correctly), or emulators that don't work with something specific (ex. PowerPC and Windows NT for PowerPC stuff. There *is* DingusPPC but still).

Additionally, if you know me, you might know I like recreating stuff. So yeah, that too.

## What does it cover?

* Typical, conventional things, like NES, or Intel 8086,
* Some perhaps more exotic things, like Zenith Z-100 stuff, Intel Itanium, or some arcade stuff,
* Some *definitely* more exotic things, like computers from before the 80s (ex. ENIAC), or cable box stuff (well, they probably don't have much in different hardware than computers, but still),
* And even other emulators, like MarioNES

However, BIOS/firmware/whatever will not be provided. There will be no recreations or anything like some later Nintendo emulators seem to have.

## Internal workings

Currently, the idea is this: things like CPUs or displays will be created separately, and whole individual devices will be made by making YAML-esque "presets" that do the full layout.

At this time, the presets format is incomplete, so I have no examples.