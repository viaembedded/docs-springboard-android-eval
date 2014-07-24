.. _smartetk:

Smart ETK
=========

VAB-600 is designed with enhanced features including Watch Dog, RTC
Power On, Programmable GPIO, and Serial Ports.

Develop Environment
-------------------

Eclipse is Android application integrated development environment (IDE)
by official recommendation. It requires to import the specific reference Java
Archive file to develop VAB-600 enhance features.

Open Eclipse IDE and create an Android project. In project properties,
import the ``smartetk.jar`` by clicking "**Add External JARs...**" into your project.

SDK Class Definitions
---------------------

All functions and values are placed in class named ``com.via.vepd.SmartETK``.
Import this package into Java code to use them.

.. _gpio:

GPIO PIN definitions
^^^^^^^^^^^^^^^^^^^^
===== == == == == == == == ==
ID    0  1  2  3  4  5  6  7
GPIO  20 21 22 23 24 25 26 27
===== == == == == == == == ==

Function Return Values
----------------------

Other than the Boolean TRUE and FALSE return values, there are eight
other types of return values found throughout the Smart ETK SDK API.

===================== =========
Error code            Constant
===================== =========
S_OK                  0
E_FAIL                -1000
E_BOARD_NOT_SUPPORT   -1001
E_ALREADY_INITIALIZED -1002
E_INVALID_ARG         -1003
E_OUT_OF_MEMORY       -1004
E_FUNC_NOT_SUPPORT    -1005
E_HARDWARE_ERROR      -1006
===================== =========

SmartETK.S_OK
^^^^^^^^^^^^^

The ``S_OK`` return value has the constant value 0. When a function
returns the ``S_OK`` value, it indicates that the function has successfully
completed.

SmartETK.E_FAIL
^^^^^^^^^^^^^^^

The ``E_FAIL`` return value has the constant value -1000. When a
function returns the ``E_FAIL`` value, it indicates that the function has
failed to complete.

SmartETK.E_BOARD_NOT_SUPPORT
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``E_BOARD_NOT_SUPPORT`` return value has the constant value -1001.
When a function returns the ``E_BOARD_NOT_SUPPORT`` value,
it indicates that the mainboard is not supported.

SmartETK.E_ALREADY_INITIALIZED
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``E_ALREADY_INITIALIZED`` return value has the constant value -1002.
When a function returns the ``E_ALREADY_INITIALIZED`` value, it
indicates that libbssjni.so has already been loaded.

SmartETK.E_INVALID_ARG
^^^^^^^^^^^^^^^^^^^^^^

The ``E_INVALID_ARG`` return value has the constant value -1003.
When a function returns the ``E_INVALID_ARG`` value, it indicates that
the arguments are invalid.

SmartETK.E_OUT_OF_MEMORY
^^^^^^^^^^^^^^^^^^^^^^^^

The ``E_OUT_OF_MEMORY`` return value has the constant value -1004.
When a function returns the ``E_OUT_OF_MEMORY`` value, it indicates
that there is insufficient memory.

SmartETK.E_FUNC_NOT_SUPPORT
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The ``E_FUNC_NOT_SUPPORT`` return value has the constant value -1005.
When a function returns the ``E_FUNC_NOT_SUPPORT`` value, it
indicates that the function is not supported on this board.

SmartETK.E_HARDWARE_ERROR
^^^^^^^^^^^^^^^^^^^^^^^^^

The ``E_HARDWARE_ERROR`` return value has the constant value -1006.
When a function returns the ``E_HARDWARE_ERROR`` value, it
indicates that there is a hardware error.

API List
--------

SmartETK.Init
^^^^^^^^^^^^^

.. c:function:: static int SmartETK.Init

   :description: This function initializes the Smart ETK and loads the JNI.
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.SupportGpio

   :description: Check if current platform supports GPIO.
   :return: * ``S_OK`` if support GPIO.
	    * ``E_FUNC_NOT_SUPPORT`` if not support GPIO.

.. c:function:: static int SmartETK.SupportWdt

   :description: Check if current platform supports watch dog timer
   :return: * ``S_OK`` if support watch dog timer
	    * ``E_FUNC_NOT_SUPPORT`` if not support watch dog timer

.. c:function:: static int SmartETK.SupportRtcWake

   :description: Check if current platform supports RTC wake-up
   :return: * ``S_OK`` if support RTC wake-up
	    * ``E_FUNC_NOT_SUPPORT`` if not support RTC wake-up

.. c:function:: GpioInfo SmartETK.Gpio_GetInfo

   :description: Gets the information of GPIO
   :return: An array representing GPIO
   :rtype: SmartETK.GpioInfo

.. c:function:: static int SmartETK.Gpio_Enable(int pinId, boolean enable)

   :description: Enable specific GPIO pin.
   :param int pinId: ID of GPIO pin. Refer to the :ref:`gpio` section for pin definition
   :param boolean enable: true for enable, false for disable
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: public static int SmartETK.Gpio_Set(int pinId, int inOut, int upDown)

   :description: Setup I/O configuration for specific GPIO pin
   :param int pinId: ID of GPIO pin. Refer to the :ref:`gpio` section for pin definition
   :param int inOut: * ``SmartETK.GM_GPI`` for input
		     * ``SmartETK.GM_GPO`` for output
   :param int upDown: * ``SmartETK.GM_NO_PULL`` for disable internal pull
		      * ``SmartETK.GM_PULL_UP`` for pull up,
		      * ``SmartETK.GM_PULL_DOWN`` for pull down.
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Gpio_Write(int pinId, int pinVal)

   :description: Set GPIO output signal
   :param int pinId: ID of GPIO pin. Refer to the :ref:`gpio` section for pin definition
   :param int pinVal: GPIO signal, 0 for logic low, 1 for logic high
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Gpio_Read(int pinId, int pinVal[])

   :description: Get GPIO input signal.
   :param int pinId: ID of GPIO pin. Refer to the :ref:`gpio` section for pin definition
   :param int[] pinVal: A single-element array returns GPIO signal. 0 for logic low, 1
			for logic high. Caller should allocate array space manually
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Wdt_SetTimer(int sec)

   :description: Set watch dog timer to specific time in second. The time should not
		 exceed the number defined by a constant ``SmartETK.WDT_MAX_SEC``
   :param int sec: time in second to reset
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Wdt_Refresh()

   :escription: Refresh the timer to the time set in Wdt_SetTimer
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Wdt_Start()

   :description: Start watch dog timer. If application does not call `Wdt_Refresh` in time
		 set in `Wdt_SetTimer`, system will be reset
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Wdt_Stop()

   :description: Stop watch dog timer
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Rtc_WakeupEnable()

   :description: Enable RTC wake-up
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Rtc_WakeupDisable()

   :description: Disable RTC wake-up
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: static int SmartETK.Rtc_SetWakeupTime(int mode, int yr, int mm, int dd, int hr, int min, int sec)

   :description: Set time to wake up by RTC
   :param int mode: * ``SmartETK.RWM_HHMM``: wake up when hour and minute match
		    * ``SmartETK.RWM_MONTH``: wake up when month day, hour and minute match
		    * ``SmartETK.RWM_WEEK``: wake up when week day, hour and minute match
   :param int yr: Year to wake up
   :param int mm: Month to wake up
   :param int dd: Day to wake up
   :param int hr: Hour to wake up
   :param int min: Minute to wake up
   :param int sec: Second to wake up
   :return: * ``S_OK`` if the function succeeds
	    * ``E_FAIL`` if the function fails

.. c:function:: native public static UartConfig Uart_GetConfig(FileDescriptor fd)

   :description: Return terminal configuration of specific FileDescriptor
   :param FileDescriptor fd: the opened file, must be a device file (under /dev)
   :return: * ``UartConfig`` if the function succeeds, see the :ref:`uart` section for detail
	    * ``null`` if the function fails

.. c:function:: native public static int Uart_SetConfig(FileDescriptor fd, UartConfig cfg)

   :description: Set terminal configuration of specific FileDescriptor
   :param FileDescriptor fd: the opened file, must be a device file (under /dev)
   :param UartConfig cfg: Terminal configuration, see the :ref:`uart` section for detail
   :return: * 0 if the function succeeds
	    * 1 if the function fails

.. _uart:

UART Parameters
---------------

SmartETK defines UART (Universal Asynchronous Receiver/Transmitter)
related values into another class`` com.via.UartConfig`` for configuration.
Instead of one-time setup for other devices, UART is transferring data
continually. Developers may blocked read, selected read, or buffered read
from UART. In order to provide developers all types of transmissions, the
APIs should be based on Java class ``java.io.FileDescriptor``.

To get FileDescriptor, the developers have to open the device file manually
(e.g. /dev/ttyS1 or /dev/ttyUSB0) with Java class ``java.io.File``. Then select a
suitable Java transmission helper class (e.g. ``java.io.FileOutputStream``).
To setup UART parameters with ``FileDescriptor`` and class ``UartConfig`` which
are provided by VIA. Please check SDK sample code for details.

Parameters in UartConfig are the same as the values in Linux Kernel.
Developers who are familiar with terminal programming in C may apply the
same macro to port existing applications to Java with UartConfig. See
Linux Programmer's Manual for details. To read the manual, enter ``man
tcsetattr`` in Ubuntu terminal.

Currently, four connection options (in struct termios) and two speed options
for Linux are available.

The four connection options are: ``c_cflag``, ``c_iflag``, ``c_oflag``, ``c_lflag``

The two speed options are: ``ispeed``, ``ospeed``

Four options will be applied with tcsetattr in Linux C library. ``c_cc[VMIN]`` is
set to 1 and ``c_cc[VTIME]`` is set to 0. ispeed and ospeed in UartConfig will
be applied to struct termios with cfsetispeed and cfsetospeed in Linux C
library.

All options have to be set before applying them. It is recommended to get
current configurations of FileDescriptor into UartConfig via
``SmartETK.Uart_GetConfig`` instead of allocating one manually.

All types of file transmissions in Java are available since we shared existing
FileDescriptor class. After FileDescriptor is configured, developers can
access UART as a normal file.
