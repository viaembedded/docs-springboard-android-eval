.. _functionality:

Functionality
=============

This chapter will describe the features supported by VAB-600 Android
evaluation image and how to evaluate these features.

Multimedia features
-------------------

To evaluate the multimedia features, you can install the following APK from
``\EVK\tools\apks\``.

* Gallery2.apk: for video and photo playback
* Music.apk: for audio playback

Network features
----------------

Configure the *Settings->Ethernet* in Android system to enable the VAB-600
on-board Ethernet function.

Miscellaneous features
----------------------

Hiding system bar
^^^^^^^^^^^^^^^^^

When the application requires display of full screen, the system bar on the
bottom area will be automatically hidden. For how to write an Android application
that can display full screen, please refer to Android official
website or the following website: http://blog.csdn.net/cjjky/article/details/6337172

ADB
^^^

VAB-600 Android BSP supports launching ``adb`` daemon when starting
Android OS. Once the Android OS has completed booting and network is
correctly configured, you can use ``adb`` to connect VAB-600, as mentioned
in section 4.4.

USB device and SD card
^^^^^^^^^^^^^^^^^^^^^^

SD card and USB devices including input devices (mouse and keyboard);
as well as storage devices (flash or hard disk), are both supported.

.. note:: The BSP cannot identify more than one USB flash/hard disk.

SmartETK Features
-----------------

SmartETK provides a set of APIs for the Android application to access the
services provided by VAB-600 hardware. The SmartETK for VAB-600 supports
the following features:

* Watch Dog
* RTC Power On
* Programmable GPIO
* Serial Ports

**WatchDog**: a timer helps the application/system to recover from dead circle
or breakdown. When it is set, it will reboot the system if no “Feeding dog”
signal is received.

**RTC Power On**: provides auto Power On feature by setting RTC auto wake
up timer.

**Programmable GPIO**: provides high level interface for the applications to
control the low level GPIO.

**Serial Ports**: provides serial port communication capability for Android
applications.

All the features can be examined through the demo application
``BoardSupportICS.apk``. The home UI of “SmartETK_sample.apk” is shown as
:num:`Figure #figure-smartetk-sample`.

.. _figure-smartetk-sample:
.. figure:: images/smartetk_sample.*
   :align: center
   :alt: Smart ETK sample app screenshot

   Smart ETK sample app screenshot

RTC Power On
^^^^^^^^^^^^

Click "RTC" to enter its UI as shown in :num:`Figure #figure-rtc-example`. Follow the steps to test
RTC function.

1. Start "SmartETK sample"
2. Enter the RTC page
3. Set date, hour and minute
4. Click "Set and Enable' button
5. Turn off the system
6. Wait for RTC auto boot

.. note::

   1. If wake-up time arrives at the same time when system is running, the system will automatically
      reboot. Please make sure the wakeup is disabled when the system is running.
   2. Please reset the wakeup time after you adjust the system time, date or timezone through
      ``Setting-> Date&Time``. Otherwise, the system may be automatically waked up on an unexpected
      time.

.. _figure-rtc-example:
.. figure:: images/rtc_example.*
   :align: center
   :alt: Smart ETK RTC Power On example screenshot

   Smart ETK RTC Power On example screenshot

WatchDog
^^^^^^^^

Click "WatchDog" to enter its UI as shown in :num:`Figure #figure-watchdog-example`. Follow the steps to
test WatchDog function.

1. Start "SmartETK sample"
2. Enter the Watch Dog page
3. Set seconds (need to refresh in # seconds, otherwise the system will reboot)
4. Click "Start" button
5. Click "Refresh" to reset timer
6. Wait for the system reboot

.. _figure-watchdog-example:
.. figure:: images/watchdog_example.*
   :align: center
   :alt: Smart ETK WatchDog example screenshot

   Smart ETK WatchDog example screenshot

GPIO
^^^^

Click "GPIO" to enter its UI as shown in :num:`Figure #figure-gpio-example`. Follow the steps to test
GPIO function.

VAB-600 provides eight GPIO pins. Test GPIO function by using
``SmartETK_sample.apk``.

There are two modes in the SamrtETK sample application.

* **Mode 1**: pin 0 to pin 3 are GPO, pin 4 to pin 7 are GPI
* **Mode 2**: pin 0 to pin 3 are GPI, pin 4 to pin 7 are GPO
* **Pull-Up**: default GPI state is pull-up
* **Pull-Down**: default GPI state is pull-down

1. Start "SmartETK sample"
2. Enter the GPIO page
3. Click "Enable" button
4. Switch between mode 1 and mode 2
5. Change GPO switch to ensure GPI status is correct

.. _figure-gpio-example:
.. figure:: images/gpio_example.*
   :align: center
   :alt: Smart ETK GPIO On example screenshot

   Smart ETK GPIO example screenshot

Serial Ports
^^^^^^^^^^^^

Click "Serial Ports" to enter its UI as shown in :num:`Figure #figure-serial-example`. Follow the steps to
test serial port function. VAB-600 supports UART 2 and external EXAR 4-channel
USB to serial device.

Use ``SmartETK_sample.apk`` to test the UART function.

1. Connect com port between VAB-600 and PC
2. Open terminal on PC site and set baud rate as 115200
3. Start "SmartETK sample"
4. Enter the UART page
5. Set dev note (ttyS2, ttyUSB0 ~ 3)
6. Click "Connect" button
7. Click "Disconnect" button

.. _figure-serial-example:
.. figure:: images/serial_example.*
   :align: center
   :alt: Smart ETK Serial Ports example screenshot

   Smart ETK Serial Ports example screenshot
