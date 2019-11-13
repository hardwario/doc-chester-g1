###########
AT Commands
###########

Both sensor device and gateway device can be controlled using AT commands over the USB interface. The USB interface provides virtual serial port (USB CDC) interface which is always available when the USB cable is plugged in.

These are the basic AT command configuration and usage rules:

* The device is further in AT commands context referred to as **MT** (Mobile Terminal).
* The host is further in AT commands context referred to as **TE** (Terminal Equipment).
* Serial port parameters are 115200 Bd, 8 data bits, no parity, 1 stop bit.
* From TE it is possible to use any new line delimiter combination combination of ``<CR>`` (0x0d) or ``<LF>`` (0x0a).
* The new line is always delimited from MT using ``<CR><LF>``.
* MT supports the possibility to clear input buffer using ``<ESC>`` key (0x1b).
* MT supports the correction of the last character using ``<BS>`` key (0x08).
* Every AT command starts with the ``AT`` string prefix.
* Some commands are part of existing standards and inspired by existing equipment.
* Vendor-specific AT commands always start with ``AT$``.
* Every command is terminated with ``OK`` in case of success, or with ``ERROR`` in case of failure.
* All commands are case-sensitive and have to follow patterns exactly described below.
* URC messages (Unsolicited Result Codes) is a kind of message, which can appear from MT at any time (these are asynchronous events).
* Messages that appear on the serial port and start with the ``#`` character, represent logging messages, which can (like URC messages) appear at any time.


***********************
Interfacing AT Commands
***********************

There are many serial port terminals that can be used to interface AT commands. For example, on macOS and Linux, you can use **picocom**. On macOS this can be easily installed using Homebrew::

   brew install picocom

Then you can start the program as::

   picocom -b 115200 --omap crcrlf --echo /dev/cu.usbserial-00001014


******************
Sensor AT Commands
******************


AT - Communication test
=======================

This command only serves the purpose to test communication with MT.

:Format:

``AT``

:Example:

::

   Command:    AT
   Response:   OK

AT&F - Restore configuration to factory defaults
================================================

This command puts the device configuration to factory default settings. It does not store the settings to non-volatile memory (see ``AT&W`` below).

:Format:

``AT&F``

:Example:

::

   Command:    AT&F
   Response:   OK

AT&W - Store configuration to non-volatile memory
=================================================

This command saves the current configuration settings to a non-volatile (EEPROM) memory.

:Format:

``AT&W``

:Example:

::

   Command:    AT&W
   Response:   OK

ATI - Request product information
=================================

This command reads the compact product information of MT.

:Format:

``ATI``

:Example:

::

   Command:    ATI
   Response:   COOPER R1.1 0.1.0
               OK

AT+CGMI - Request manufacturer identification
=============================================

This command reads the manufacturer identification of MT.

:Format:

``AT+CGMI``

:Example:

::

   Command:    AT+CGMI
   Response:   HARDWARIO s.r.o.
               OK

AT+CGMM - Request model identification
======================================

This command reads the model identification of MT.

:Format:

``AT+CGMM``

:Example:

::

   Command:    AT+CGMM
   Response:   COOPER R1.1
               OK

AT+CGMR - Request revision identification
=========================================

This command reads the serial number of MT.

:Format:

``AT+CGMR``

:Example:

::

   Command:    AT+CGMR
   Response:   0.1.0
               OK

AT+CGSN - Read serial number identification
===========================================

This command reads the serial number (id) of MT.

:Format:

``AT+CGSN``

:Example:

::

   Command:    AT+CGSN
   Response:   0123456789012345
               OK

AT+CLAC - List available AT commands
====================================

This command lists all available AT commands.

:Format:

``AT+CLAC``

:Example:

::

   Command:    AT+CLAC
   Response:   AT
               AT&F
               ...
               OK

AT$CHANNEL - Set/read radio channel
===================================

This command allows to set or read radio channel. The supported range of channels is 0..19. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$CHANNEL?``

``AT$CHANNEL=<channel>``

:Example:

::

   Command:    AT$CHANNEL?
   Response:   $CHANNEL: 0
               OK

   Command:    AT$CHANNEL=1
   Response:   OK

AT$KEY - Set encryption key (AES-128)
=====================================

This command allows setting key for encrypted radio communication. It expects the key in the hexadecimal format (32 characters). The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$KEY=<key>``

:Example:

::

   Command:    AT$KEY=f2e891014be3e94151c66249203e2246
   Response:   OK

AT$STATUS - Retrieve device status
==================================

This command retrieves the current device status.

:Format:

``AT$STATUS``

:Example:

::

   Command:    AT$STATUS
   Response:   $STATUS: "Acceleration",0.11,0.00,0.96
               $STATUS: "Altitude",321.8
               $STATUS: "CO2 Concentration"
               $STATUS: "Humidity",48.4
               $STATUS: "Illuminance",28
               $STATUS: "Orientation",1
               $STATUS: "Press Count",0
               $STATUS: "Pressure",97521
               $STATUS: "Sound Level",0
               $STATUS: "Temperature",24.64
               $STATUS: "VOC Concentration"
               $STATUS: "Voltage",0.01
               OK

AT$SEND - Send data
===================

This command send data immediately.

:Format:

``AT$SEND``

:Example:

::

   Command:    AT$SEND
   Response:   OK

AT$PULSE - Pulse LED
====================

This command pulses LED on MT for 3 seconds.

:Format:

``AT$PULSE``

:Example:

::

   Command:    AT$PULSE
   Response:   OK

AT$BEEP - Beep speaker
======================

This command run beep speaker on MT for 3 seconds.

:Format:

``AT$BEEP``

:Example:

::

   Command:    AT$BEEP
   Response:   OK

AT$HELP - List help
===================

This command lists AT command help.

:Format:

``AT$HELP``

:Example:

::

   Command:    AT$HELP
   Response:   AT&F Restore configuration to factory defaults
               AT&W Store configuration to non-volatile memory
               ...
               AT$HELP Print this help
               OK

AT$LOCK - Lock configuration
============================

This command allows setting password and lock configuration to the read-only mode. It expects a parameter of up to 12 ASCII characters - all printable characters inside the quotation marks are allowed. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$LOCK="<password>"``

:Example:

::

   Command:    AT$LOCK="jzvuK5oTwBs6"
   Response:   OK

AT$UNLOCK - Unlock configuration
================================

This command allows removing password and unlock configuration. It expects a parameter of up to 12 characters - all printable characters inside the quotation marks are allowed. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$UNLOCK="<password>"``

:Example:

::

   Command:    AT$UNLOCK="jzvuK5oTwBs6"
   Response:   OK

AT$CONFIG - Configuration
=========================

This command allows configuration some parameters. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$CONFIG``

``AT$CONFIG="<name>",<value>``

:Parameters:

* ``Report Interval`` uint: seconds, default: 300, min: 30, max: 65535

:Example:

::

   Command:    AT$CONFIG
   Response:   $CONFIG: "Report Interval",300
               OK

   Command:    AT$CONFIG="Report Interval",600
   Response:   OK


******************
Dongle AT Commands
******************

The following AT commands are supported on the gateway device.

AT$LIST - List nodes
====================

This command prints whitelist of all the nodes.

:Format:

``AT$LIST``

:Example:

::

   Command:    AT$LIST
   Response:   $CONFIG: "Report Interval",300
               OK

   Command:    AT$LIST
   Response:   0123456789012345,"Room 1"
               5432109876543210,""
               OK

AT$ATTACH - Attach new node
===========================

This command adds a new node to the whitelist. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$ATTACH=<id>,<key>,"<alias>"``

``AT$ATTACH=<id>,<key>``

:Example:

::

   Command:    AT$ATTACH=0123456789012345,f2e891014be3e94151c66249203e2246,"Room 1"
   Response:   OK

AT$DETACH - Detach existing node
================================

This command removes the existing node from the whitelist. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$DETACH=<id>``

:Example:

::

   Command:    AT$DETACH=0123456789012345
   Response:   OK

AT$PURGE - Remove all paired nodes
==================================

This command deletes all paired nodes. The command affects configuration settings, which have to be permanently stored using the ``AT&W`` command.

:Format:

``AT$PURGE``

:Example:

::

   Command:    AT$PURGE
   Response:   OK


*******************
Sensor URC Messages
*******************

$BOOT - Device restart
======================

This URC informs TE about the MT restart.

:Format:

``$BOOT``

$PRESS - Push button press
==========================

This URC informs about the push button press event. It provides a number of press events.

:Format:

``$PRESS: <count>``


*******************
Dongle URC Messages
*******************

$BOOT - Device restart
======================

This URC informs TE about the MT restart.

:Format:

``$BOOT``

$RECV - Message from node
=========================

This URC provides extracted message information from the node.

:Format:

``$RECV: <p01>,<p02>,...<p15>``

:Parameters:

* ``<p01>`` rssi
* ``<p02>`` id
* ``<p03>`` sequence
* ``<p04>`` altitude
* ``<p05>`` co2_conc
* ``<p06>`` humidity
* ``<p07>`` illuminance
* ``<p08>`` motion_count
* ``<p09>`` orientation
* ``<p10>`` press_count
* ``<p11>`` pressure
* ``<p12>`` sound_level
* ``<p13>`` temperature
* ``<p14>`` voc_conc
* ``<p15>`` voltage

.. note:: If some parameter is missing, it means it is invalid (sensor is not yet ready, or sensor is broken).
