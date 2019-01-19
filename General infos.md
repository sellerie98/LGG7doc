# General infos about the LG G7 ThinQ and modifications

## Intro
The first thing that has to be said here is: Right at the moment, there is no known way of unlocking bootloaders of other LG G7 ThinQs besides the LMG710EM (global) variant, also its practically impossible to generate an own unlock file or , because its not known what it even is. 

Obtaining a boot image is not just needed for getting TWRP to work, but also for rooting purposes:
When booting the phone normally, without pressing any buttons, the phone uses the kernel from the boot image,
but uses the initrd from the depending /system partition.
When using the usual button combo (holding vol-  and power while turning it on, then letting go of the power button for half a sec) the phone uses the kernel from the boot image and the initrd from the boot image instead, which makes it easily possible to build a boot image that contains TWRP.

There is a tool that is capable of unpacking modern KDZ files, e.g. for the LGG7: [KDZtools by ehem](https://github.com/ehem/kdztools)

Mutliple people besides me have started archiving partitions and boot images for the purpose of documentation and fiddling thanks to this.
