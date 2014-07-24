.. _booting:

Making System Booting Media
===========================

Update VAB-600 Firmware
-----------------------

Steps for Firmware update:

1. Unpack the firmware installer image file to SD card.
2. Power off VAB-600
3. Insert SD card
4. Power on VAB-600
5. The installer will update firmware automatically
6. Remove SD card when update is finished
7. System will reboot in 3 seconds

2.2. Change U-boot default configuration
----------------------------------------

1. Open [firmware installer image]/bspinst/bspinst.cfg file.
2. Find section [VIA_RDK]
3. Disable default setting by adding the remark "#"
4. Change to new setting by removing the remark “#”

For example, change HDMI to LVDS. Default::

  # HDMI
  setenv wmt.display.param 4:6:1:1280:720:60
  # LVDS
  #setenv wmt.display.param 2:0:24:800:480:60

Change to::

  # HDMI
  #setenv wmt.display.param 4:6:1:1280:720:60
  # LVDS
  setenv wmt.display.param 2:0:24:800:480:60
