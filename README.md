Multi-ISO USB
=============

Boot multiple ISO images from a single USB stick using GRUB.

This repository includes a `grub.cfg` file with entries for the
following ISO images:

- `ubuntu-12.10-desktop-amd64.iso`
- `linuxmint-14.1-cinnamon-dvd-64bit.iso`
- `linuxmint-201303-cinnamon-dvd-64bit-rc.iso`
- `crunchbang-11-20130119-amd64.iso`
- `grml96-full_2012.05.iso`
- `systemrescuecd-x86-3.4.1.iso` (2 entries: 32-bit and 64-bit)

How to Create the Bootable USB
------------------------------

 1. Create a bootable FAT32 partition on an unmounted USB stick that
    is large enough for all the ISO images you want to include.

    Use the label "`multiboot`". The label is used by some entries to
    identify the partition and find ISO).

    Example, where `/dev/sdX1` is the newly created partition:

        $ mkfs.vfat -n multiboot /dev/sdX1

 2. Mount the newly created partition and create the two directories
 `boot` and `iso`:

        $ cd <mount-point>
        $ mkdir boot iso

 3. Install GRUB on the USB stick:

        $ grub-install --force --no-floppy --boot-directory=<mount-point>/boot /dev/sdX

 4. Put the ISO images in the `iso` directory on the USB stick.

 5. Copy the `grub.cfg` file in this repository to
 `<mount-point>/boot/grub/grub.cfg`


Credits:
[Transform a USB stick into a boot device packing multiple Linux distros using GRUB](http://www.circuidipity.com/multi-boot-usb.html)
