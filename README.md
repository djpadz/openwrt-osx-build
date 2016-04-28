openwrt-bootstrap-files
=======================

These scripts will help you create a build environment for OpenWRT, without having to build inside of a Linux VM.

You need:

* [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)
* [Homebrew](http://brew.sh/)

You **do not need**:

* Root access (to build OpenWRT).  Run everything as a normal user.  You will, however, need root (or sudo) to use the `flash` script.

To use:

1. Create a sparse disk image, with a **case sensitive** filesystem.
```
$ hdiutil create -size 24g -fs 'Case-sensitive HFS+' -type SPARSEBUNDLE -nospotlight -volname OpenWRT-build OpenWRT-build
```
* Clone this repo into the root of the mounted filesystem.
```
$ git clone https://github.com/djpadz/openwrt-osx-build.git .
```
* `$ ./bootstrap`

For future builds:

1. Mount the filesystem.
* `cd` to the mounted filesystem's root.  (For example, `$ cd /Volumes/OpenWRT-build`)
* `$ . ow-env`
* `$ ./update`
* `$ cd openwrt`
* `$ make menuconfig`
* `$ make`

For more information on building OpenWRT, see [The OpenWRT developer documentation](https://wiki.openwrt.org/doc/playground/developer).

To flash the image to a card, use the `flash` script.

1. Mount your flash card on your computer.
* `# ./flash`
* If it cannot figure out which device to use, then you may have to tell it manually.  For example: `# ./flash disk3`

**Be very careful, when using the `flash` script!**  The script uses `dd` to overwrite the contents of the specified device.  Used incorrectly, it could very possibly erase your hard drive!
