#General infos about the LG G7 ThinQ and modifications

#Intro
The first thing that has to be said here is: Right at the moment, there is no known way of unlocking bootloaders of other LG G7 ThinQs besides the LMG710EM (global) variant, also its practically impossible to generate an own unlock file or , because its not known what it even is.


Regarding the LG G7 rooting, there is a significant bootstrapping problem at the moment:
Even though the bootloader is unlocked, we're still not able to obtain a boot image to modify,
because we still cannot get raw access to any of the partitions, without either
	1. unpacking a dumped KDZ file that is obtained by scraping the cache of LG bridge (Winodws and Mac)
	2. Opening up the hardware and access the chip directly
	3. Exploiting Android

# Why this is needed

Obtaining a boot image is not just needed for getting TWRP to work, but also for rooting purposes:
When booting the phone normally, without pressing any buttons, the phone uses the kernel from the boot image,
but uses the initrd from the depending /system partition.
But when using the usual button combo (holding vol-  and power while turning it on, then letting go of the power button for half a sec) the phone uses the kernel from the boot image and the initrd from the boot image instead.

## 1.
Noone I know that works on LG G7 ThinQ that I know was able to unpack the KDZ files that came out of LG bridge yet, so this is not possible at the moment.

## 2.
The phone is currently still very expensive, so noone I know was yet able to afford buying a second G7 to disassemble it.
Especially regarding that LG made the step to fullbody it and make it waterproof, which increases the required effort.

## 3.
Gladly, a user I prefer to keep anonymous here, was able to obtain root privilegues on a G7 ThinQ,
therefore it was possible to obtain a dump of the boot image (and all other partitions) so its now possible
for some people to fiddle around and create modified boot images.
The problem is that its necessary to rely on foreign sources to obtain an image to modify this way.

Mutliple people besides me have started archiving partitions and boot images for the purpose of documentation and fiddling thanks to this.
