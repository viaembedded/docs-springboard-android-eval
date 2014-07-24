.. _image:

Build and Install VIA Image
===========================

Build Kernel
------------

The Android file system works based on Linux kernel::

  $ cd << Work _DIR>>/kernel_3.0.8
  $ make Android_defconfig
  $ make clean
  $ make

Build U-Boot
------------

The u-boot will initiate basic hardware and load kernel into memory::

  $ cd <<Uboot_DIR>>/uboot.130522
  $ make wmt_config
  $ make
