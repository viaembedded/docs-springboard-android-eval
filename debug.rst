.. _debug:

Debug Message
=============

U-Boot Parameters
-----------------

There is default parameters file in the firmware installer:

  $(SD card)/bspinst/bspinst.cfg

The ``bspinst.cfg`` file structure has four segments.

* **Scenario**: board model and boot method
* **Common**: general setting
* **Target (board models)**: specific setting for each target
* **Routine**: parameters of boot method

U-Boot Environment
------------------

VAB-600 android platform can stop booting to enter u-boot environment.
The u-boot will initiate hardware at earlier stage by those parameters.

Connect to the debug port using terminal application on PC site.

.. _figure-rs232:
.. figure:: images/rs232.*
   :align: center
   :alt: Debug connection schematic

   Debug connection

.. _figure-rs232-cable:
.. figure:: images/rs232_cable.*
   :align: center
   :alt: Springboard with RS232 debug cable

   Springboard with RS232 debug cable

The serial connection settings::

  Comm speed: 115200
  Comm parity: None
  Comm data: 8
  Comm stopbits:1

Enter u-boot
^^^^^^^^^^^^
The u-boot will wait 3 seconds to stop booting after power on by pressing
any key. When booting is stopped, the prompt sign ``WMT #`` will be shown
on terminal screen.

U-Boot is like a tiny operation system that has its own commands. Here it
describes some important commands and parameters.

U-Boot Parameters Example
-------------------------

Print online help::

  WMT # help

Change display mode and resolution:

* LVDS output::

    WMT # setenv wmt.display.param 2:0:24:800:480:60

* HDMI output ::

    WMT # setenv wmt.display.param 4:6:1:1280:720:60

* Save changed parameters::

    WMT # saveenv

Setup ADB
---------

The ADB is the debug tool for Android application development.

* PC and VAB-600 must be in the same network domain
* Connect PC to VAB-600
    * PC site: ``$ ./adb tcp``
    * PC site: ``$ ./adb connect [VAB-600 IP]``
* Install application
    * PC site: ``$ ./adb install [name].apk``
* Test Shell
    * PC site: ``$ ./adb shell ls``
    * PC site: ``$ ./adb shell ls -l``
