.. _build:

==================
Build from sources
==================

.. _build-linux:

Linux kernel
------------

.. _build-u-boot:

U-boot
------

.. _build-gen-update-image:

Generate update image
---------------------

We provide a utility scripts to generate an update image that can be used update the firmware on the device. See :ref:`getting-started-firmware-update`


Clone repository containing scripts (this is a private repository)::

    $ git clone https://github.com/hostmobility/mx4.git -b mx4-2.0

Enter the repository::

    $ cd mx4

To be able to generate an image you must have access to binaries (Linux kernel, u-boot, root filesystem). You can build them by following the instructions in :ref:`build-yocto`.

To generate update image::

    $ ./make_system.sh -t t30 -r ../Angstrom-console-hostmobility-image-glibc-ipk-v2016.12-mx4-t30.rootfs.tar.xz -k ../uImage

A break down of the above arguments:

* **-t 30** - This sets the system type to **t30** which is equivalent to MX-4 T30
* **-r** - Path to root file-system tarball. This will be un-packed to generate an binary form depending on filesystem type. MX-4 T30 uses ext3. Most other products use NAND flash and UBI/UBIFS.
* **-k** - Path to Linux kernel image.

When you have succesully executed the script it shall have generated an deploy directory::

    deploy/
    ├── bin
    ├── release
    └── rootfs

* **bin** - Contains a copy of all input binaries
* **release** - Contains the update image together with all scripts and files necessarry to re-create the update image
* **rootfs** - Unpacked root file-system tarball

Lets take a close look at the release directory::

    deploy/release/
    ├── boot.vfat
    ├── mbr.bin
    ├── production_rootfs.tar.bz2
    ├── rootfs.ext3
    ├── t30_hmupdate.img
    ├── uImage
    └── update_tools

* **boot.vfat** - Binary representation of "boot partition" containing Linux kernel image + dtb (only exists on devices that boot from eMMC)
* **mbr.bin** - Partition table (only exists on devices that boot from eMMC)
* **production_rootfs.tar.bz2** - Copy of input root file-system tarball
* **rootfs.ext3** - Binary representation of root file-system
* **t30_hmupdate.img** - This is the image that you can use to update your device (contains everything else that is in this folder). Name can vary depending on which system type is set. Always named hmupdate.img, but with a different prefix.
* **uImage** - Copy of input Linux kernel image
* **update_tools** - Scripts that are used to generate the t30_hmupdate.img above.

The utility script does provide a lot of "switches" and all of them are optional. In teory you can create an update image that does not update anything::

    $ ./make_system.sh 
    Usage: make_system.sh
        -e - Ship U-Boot Environment file
        -k - Path to kernel binary
        -p - Path to gziped bmp splash screen image
        -P - Skip PIC upgrade
        -r - Path to rootfs tar.gz generated with Yocto/OE-core
        -t - system type (mx4, v61, c61, vcc, t20, t30, consat, ct, mil or gtt)
        -u - Path to U-Boot binary

    Example: ./make_system.sh -t t20 -k <path to kernel> -b <path to U-boot binary> -r <path to rootfs archive>i


