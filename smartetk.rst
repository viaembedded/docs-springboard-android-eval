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

GPIO PIN definitions:

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
