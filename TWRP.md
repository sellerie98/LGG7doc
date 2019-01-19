# How to compile TWRP for your device with a self compiled or prebuilt kernel

##Intro
Installing TWRP on the LG G7 is a little bit different than on other devices:
The TWRP (which majorly consits of an initrd) image is not to be installed in a recovery partitition or similar, but directly into the boot image:
When using the button combo or the `reboot recovery` command in adb shell, instead of the ramdisk image in /system, the ramdisk from the boot image is used.
This makes it possible for us to install TWRP to the device by modifying the boot image.


## How to compile TWRP for G7

### Requirements
	- A linux box (I recommend Debian) (A Virtualbox VM is also ok)
	- About 20GB of storage
	- several tools: `abootimg repo m4 bison flex build-essential` (on Debian)
	- ccache (Even though this is fully optional)
	

### getting the required files
The guide from [Dees_troy is prett straighforward.](https://forum.xda-developers.com/showthread.php?t=1943625) That's why I oriented myself on this one.

I'd recommend using the minimal manifest as this is enough to build twrp properly.
Cloning it with git is noot needed. Use Google's repo tool, which you can find in the debian/ubuntu repos.
If you cannot find it in the repos of your distro, you can still get it from [here](https://gerrit.googlesource.com/git-repo/).

After getting this tool, get the minimal manifest linked in the guide (branch android-8.0), by following the procedures listed in the README of it.

When this is done, create the folders `device/lge/judy` (`mkdir -p device/lge/judy`) in the same folder you downloaded the manifest into.

Navigate into `device/lge/judy` and clone the following repo into the folder: `https://github.com/sellerie98/android_device_lge_judy`.

### Building
Now go back and setup the build enviroment:
	- `sudo apt install ccache` (This step is optional, but speeds up recompilations immensely, also it's only needed if its not installed yet)
	- `export LC_ALL=C`
	- `export USE_CCACHE=1` (Only do this if you decided to use ccache and have it installed)
	- `. ./build/envsetup.sh`
	- `lunch omni_judy-eng`
	- `make bootimage -j?` (Replace the ? with the number of the threads the device you're currently building on has +1)

This will take a while, but after that, you should have a bootimage.
This bootimage will most probably not work, so don't flash it yet! 

### Preparing the boot image
You need to modify any original boot image to make it work.
You can obtain these by getting a KDZ file (e.g. the one that autoprime posted [here](https://forum.xda-developers.com/lg-g7-thinq/development/dump-g7-stock-vendor-t3840834) and extracting it with kdztools mentioned in the 'General infos.md' file.
For that we use `abootimg`:
	- Create an empty folder and copy the twrp image and the original boot image into it
	- extract the twrp image: `abootimx -x <twrp image>
	- replace the initrd in the original image with TWRP: `abootimg -u <original image> -r initrd.img`

And voilá! There we have a LG G7 ThinQ boot image capable of booting TWRP and the respective android version (depending on the version you got the boot image from).
