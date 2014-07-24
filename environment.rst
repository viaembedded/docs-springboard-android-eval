.. _environment:

Setting Up Environment
======================

The Android build system does not compile kernel on-fly. It only contains a
prebuilt kernel binary which will be added to the target image. This
approach may be good enough for the arm emulator target, but not suitable
for VAB-600 platforms. The VAB-600 platforms have various hardware
features. The kernel binary and its modules may need to be adjusted at
compile time or runtime.

This section will describe the process of how to setup build environment for
Linux kernel source and Android Framework source. That is the ability to
build kernel and modules by a predefined or customized configuration
during the building process.

Setting Development Environment
-------------------------------

Operating System: Ubuntu 12.04 LTE.

Install tool chain.

1. Unpack arm_201103_gcc4.5.2.tgz to <TOOLPATH>
2. Add path "<TOOLPATH>/arm_201103_gcc4.5.2/mybin" in environment setting

Example::

  ~$ mkdir tools
  ~$ tar -zxf arm_201103_gcc4.5.2.tgz -C tools
  ~$ vi .bashrc
  add: export PATH=/home/xxx/tools/arm_201103_gcc4.5.2/mybin:$PATH
  save and exit
  reboot system

Prepare the Source Tree
-----------------------

The Android BSP is packed with tgz file. Unpack sources to each directory.

Unpack VAB-600 Android BSP source::

  $ tar -zxf kernel_3.0.8.tar.gz -C <<Work_DIR>>
  $ tar -zxf uboot.130522.tar.gz -C << Work _DIR>>
