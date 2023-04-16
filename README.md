# asusk6500ze-linux
This repo shows how well does Asus Vivobook Pro 15 (K6500ZE) support Linux, lol

# Specs
Hardware | Device
-------- | ------
CPU | Intel i7-12650H (4.7GHz)
GPU | Nvidia RTX 3050 Ti Mobile 60W
RAM | 16 GB DDR5
SSD | NVME INTEL SSDPEKNW010T8 1 TB
Screen | 15.6' 1920x1080 OLED

## What works
```Everything, that isn't listed in the "doesn't work" section, lmao```
## What works, but with a little bit of a tweaking
Thingy | Fix | ?
------ | --- | ---
Audio | ```hda-verb /dev/snd/hwC0D0 0x20 0x500 0x1b && hda-verb /dev/snd/hwC0D0 0x20 0x477 0x4a4b && hda-verb /dev/snd/hwC0D0 0x20 0x500 0xf && hda-verb /dev/snd/hwC0D0 0x20 0x477 0x74``` | ...
CPU throttling | Install [*throttled*](https://github.com/erpalma/throttled) and change the limits to 115W | For some reason, CPU is throttled when it goes above 27W, lol
## What works, but does it kinda shitty xd
Thingy | Reason
------ | ------
C-states | Don't actually what causes that, but on all distributives, except Ubuntu, power state of the CPU doesn't go lower than C2. On Ubuntu, you're able to do that, though if you won't start the laptop without charger, it simply locks itself at C3 and doesn't go lower than that. Probably it's because of the ACPI states, I am not actually sure
## What doesn't work
Device | ID | Reason
------ | -- | ------
Fingerprint reader | 2808:a658 | no driver for the device
Camera switch button | ... | ?
Screenshot button | ... | ?
## Some additional information
If you're using dual monitor setup, then you should probably switch to the dedicated graphics, because Wayland and X11 are lagging (like, really) with hybrid graphics. Not a laptop issue, but still.
