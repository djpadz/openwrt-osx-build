openwrt-bootstrap-files
=======================

You need:

* [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)
* [Homebrew](http://brew.sh/)

You **do not need**:

* Root access (to build OpenWRT).  Run all of this as a normal user.  You will, however, need root (or sudo) to use the `flash` script.

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
* `cd` to the mounted filesystem's root.
* `$ . ow-env`
* `$ ./update`
* `$ cd openwrt`
* `$ make menuconfig`
* `$ make`

To flash the image to a card, use the `flash` script.

1. Mount your flash card on your computer.
* `# ./flash`
* If it cannot figure out which device to use, then you may have to tell it manually.  For example: `# ./flash disk3`
