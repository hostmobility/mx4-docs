.. _build-yocto:

=============
Yocto/OE-core
=============

We utilize the `Yocto project <https://www.yoctoproject.org/>`_ to generate a root file-system, Linux kernel binary, U-boot binary and toolchain (SDK).

It is recommended that you have an powerful host machine that is used for BSP builds with Yocto/OE-core. The build usually takes a few hours the first time you run it, subsequent builds take minutes (depending on what changes you have made)

We provide a manifest file that can be used together with `Google repo <https://source.android.com/source/using-repo>`_. 

Check `here <https://github.com/hostmobility/hostmobility-bsp-platform>`_ for further instructions on how to setup and build with Yocto/OE-core.

