# asusk6500ze-linux
This repo shows how well does Asus Vivobook Pro 15 (K6500ZE) support Linux.

# Specs
Hardware | Device
-------- | ------
CPU | Intel i7-12650H (4.7GHz)
GPU | Nvidia RTX 3050 Ti Mobile 65W
RAM | 16 GB DDR5
SSD | NVME INTEL SSDPEKNW010T8 1 TB
Screen | 15.6' 1920x1080 OLED

## What works
```Everything, that isn't listed in the "doesn't work" section, lmao```
## What works, but with a little bit of a tweaking
Thingy | Fix | ?
------ | --- | ---
Audio | ```hda-verb /dev/snd/hwC0D0 0x20 0x500 0x1b && hda-verb /dev/snd/hwC0D0 0x20 0x477 0x4a4b && hda-verb /dev/snd/hwC0D0 0x20 0x500 0xf && hda-verb /dev/snd/hwC0D0 0x20 0x477 0x74``` | ...
CPU throttling | Install [*throttled*](https://github.com/erpalma/throttled) and change the limits to 115W | For some reason, CPU is throttled when it goes above 27W
Sleep* | Enter ```mem_sleep_default=deep``` in GRUB_CMDLINE_LINUX_DEFAULT | s2idle consumes a bit more battery compared to deep sleep

<sub>*breaks PKG C-States if used</sub>
## What works, but does it weirdly
Thingy | Reason
------ | ------
PKG C-States | They're going to work properly only if you will start the laptop without the charger. If you're going to launch your laptop **with** a charger, prepare to weirdass bugs with it, although it won't affect the actual performance. Also, they won't go below C2 after reboot
GPU Fan(?) | It works, but you aren't able to tweak it nor set the fan levels
## What doesn't work
Device | ID | Reason
------ | -- | ------
Fingerprint reader | 2808:a658 | no driver for the device
Camera switch button + LED | ... | ?
Screenshot button | ... | ?
Microphone button (LED) | ... | ?
## Some additional information
To make this laptop able to enter C9/C10 states more frequently add ```i915.enable_psr=1``` to kernel parameters.

If you're using dual monitor setup, then you should probably switch to the dedicated graphics, because Wayland and X11 are lagging (like, really) with hybrid graphics. Not a laptop issue, but still. 

To change GPU power limit, you need to write `sudo nvidia-smi -pl (amount)`.

To change battery charge threshold, you need to write ```echo (amount) > /sys/class/power_supply/BAT0/charge_control_end_threshold```.
