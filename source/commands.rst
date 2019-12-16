###########
AT Commands
###########

* AT commands begin with ``AT``.
* AT commands starting with ``AT$`` are vendor-specific.
* Each command as well as response is terminated by ``<LF>``.
* The response can have multiple lines in the output.
* The last response message is either ``OK`` or ``ERROR: "<message>"``.
* During command processing, other result messages (URC) can appear.
* URC messages start with the ``@`` symbol.


***********************
Interfacing AT Commands
***********************

There are 2 options to interface the AT commands:

1. Using Bluetooth and **Bluefruit LE Connect** mobile app from Adafruit.
2. Via **SEGGER** J-Link and the RTT console.

.. note::

   The Bluefruit app is available both on App Store and Google Play.


********************
Standard Command Set
********************


AT - Basic communication test
=============================

:Format:

``AT``

:Example:

::

   Command:    AT
   Response:   OK


ATI - Request product information
=================================

:Format:

``ATI``

:Example:

::

   Command:    ATI
   Response:   CHESTER R2.0 v2.1.0
               OK

AT&F - Factory default reset
============================

:Format:

``AT&F``

:Example:

::

   Command:    AT&F
   Response:   OK


AT&W - Store configuration to NVM
=================================

:Format:

``AT&W``

:Example:

::

   Command:    AT&W
   Response:   OK

AT+CGMI - Request manufacturer identification
=============================================

:Format:

``AT+CGMI``

:Example:

::

   Command:    AT+CGMI
   Response:   +CGMI: "HARDWARIO s.r.o."
               OK


AT+CGMM - Request model identification
======================================

:Format:

``AT+CGMI``

:Example:

::

   Command:    AT+CGMM
   Response:   +CGMM: "CHESTER"
               OK


AT+CGMR - Request revision identification
=========================================

:Format:

``AT+CGMR``

:Example:

::

   Command:    AT+CGMR
   Response:   +CGMR: "R2.0"
               OK


AT+CGSN - Request product serial number identification
======================================================

:Format:

``AT+CGSN``

:Example:

::

   Command:    AT+CGSN
   Response:   +CGSN: "1A:2B:3C:4D:5E:6F"
               OK


AT+CLAC - List all available AT commands
========================================

:Format:

``AT+CLAC``

:Example:

::

   Command:    AT+CLAC
   Response:   ...
               OK

..
  TODO: Provide full example listing


******************
Custom Command Set
******************


AT$CONFIG - Get full configuration data
=======================================

:Format:

``AT$CONFIG``

:Example:

::

   Command:    AT$CONFIG
   Response:   $CONFIG: "ENEH",0
               $CONFIG: "ENET",0
               $CONFIG: "ENIH",0
               $CONFIG: "ENIT",0
               $CONFIG: "ENOD",0
               $CONFIG: "ENPB",0
               $CONFIG: "ENPC",0
               $CONFIG: "ENPT",0
               $CONFIG: "ENSS",0
               $CONFIG: "ENVM",0
               $CONFIG: "NBAP","hardwario.com"
               $CONFIG: "NBPI",23003
               $CONFIG: "NBSP",""
               $CONFIG: "NBUA","192.168.168.1"
               $CONFIG: "NBUP",4008
               $CONFIG: "RIHB",86400
               $CONFIG: "RISR",3600
               OK

:Details:

* ``ENEH``: Enable ext. hygrometer
* ``ENET``: Enable ext. thermometer
* ``ENIH``: Enable int. hygrometer
* ``ENIT``: Enable int. thermometer
* ``ENOD``: Enable orientation detector
* ``ENPB``: Enable push button
* ``ENPC``: Enable pulse counter
* ``ENPT``: Enable position tracker
* ``ENSS``: Enable soil sensor
* ``ENVM``: Enable voltage monitor
* ``NBAP``: NB-IoT APN
* ``NBPI``: NB-IoT PLMN ID
* ``NBSP``: NB-IoT SIM PIN
* ``NBUA``: NB-IoT server UDP IP address
* ``NBUP``: NB-IoT server UDP port
* ``RIHB``: Report interval for heartbeat
* ``RISR``: Report interval for sensors

.. note::

   Configuration has to be saved with the ``AT&W`` command.


AT$BLUETOOTH - Get full Bluetooth data
======================================

:Format:

``AT$BLUETOOTH``

:Example:

::

   Command:    AT$BLUETOOTH
   Response:   $BLUETOOTH: "BDADDR","1A:2B:3C:4D:5E:6F"
               $BLUETOOTH: "PROTOCOL",1
               $BLUETOOTH: "CLIENTS",1
               OK


AT$NETWORK - Get full network data
==================================

:Format:

``AT$NETWORK``

:Example:

::

   Command:    AT$NETWORK
   Response:   $NETWORK: "IMEI",165051601180335
               $NETWORK: "IMSI",901288001062003
               $NETWORK: "IPAD","10.0.0.1"
               OK

..
  TODO: Insert the real IMEI (the one above is a random number)


AT$STATUS - Get full device status
==================================

:Format:

``AT$STATUS``

:Example:

::

   Command:    AT$STATUS
   Response:   $STATUS: "ACCX",0.815
               $STATUS: "ACCY",0.024
               $STATUS: "ACCZ",-0.987
               $STATUS: "DUPT",168462
               $STATUS: "EHRH",48.9
               $STATUS: "EHTM",23.1
               $STATUS: "ETTM",22.5
               $STATUS: "IHRH",49.2
               $STATUS: "IHTM",23.0
               $STATUS: "ITTM",22.7
               $STATUS: "ODON",1
               $STATUS: "PBST",0
               $STATUS: "PCTC",1227
               $STATUS: "PTFQ",2
               $STATUS: "PTLA",50.596406
               $STATUS: "PTLO",15.229035
               $STATUS: "PTST",1
               $STATUS: "PTTM",1574069695
               $STATUS: "SSMO",6789
               $STATUS: "SSTM",4.8
               $STATUS: "VMVO",-2.64

:Details:

* ``DUPT``: Device uptime
* ``ACCX``: Accelerometer - acceleration in X-axis
* ``ACCY``: Accelerometer - acceleration in Y-axis
* ``ACCZ``: Accelerometer - acceleration in Z-axis
* ``EHRH``: External hygrometer - relative humidity
* ``EHTM``: External hygrometer - temperature
* ``ETTM``: External thermometer - temperature
* ``IHRH``: Internal hygrometer - relative humidity
* ``IHTM``: Internal hygrometer - temperature
* ``ITTM``: Internal thermometer - temperature
* ``ODON``: Orientation detector - orientation
* ``PBST``: Push button - status (``1`` = pressed)
* ``PCTC``: Pulse counter - total count
* ``PTFQ``: Position tracker - last known fix quality (``0`` = no fix, ``1`` = 2D fix, ``2`` = 3D fix)
* ``PTLA``: Position tracker - last known latitude
* ``PTLO``: Position tracker - last known longitude
* ``PTST``: Position tracker - current status (``1`` = on)
* ``PTTM``: Position tracker - last known UTC time
* ``SSMO``: Soil sensor - moisture
* ``SSTM``: Soil sensor - temperature
* ``UPTM``: Device uptime
* ``VMVO``: Voltage monitor - voltage


AT$REBOOT - Reboot device
=========================

:Format:

``AT$REBOOT``

:Example:

::

   Command:    AT$REBOOT
   Response:   OK


AT$RECONNECT - Reconnect to NB-IoT network
==========================================

:Format:

``AT$RECONNECT``

:Example:

::

   Command:    AT$RECONNECT
   Response:   OK


AT$DFU - Switch device to bootloader
====================================

:Format:

``AT$DFU``

:Example:

::

   Command:    AT$DFU
   Response:   OK

.. warning::

   After this command, the device will switch to bootloader and will be available with a different BDADDR - i.e. the lowest byte of the BDADDR is incremented by one (only the lowest byte, the carry does not overflow to the upper bytes).
