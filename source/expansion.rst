#################
Expansion Modules
#################

CHESTER is an extensible device throughout the expansion modules (up to two) installed underneath the bottom side of the board (underneath the battery).

***********
CHESTER-X0A
***********

This module adds the possibility to connect external I2C peripherals. For instance temperature/humidity sensor.

***********
CHESTER-X0B
***********

This module adds the possibility to connect external ultrasonic sensor which can be used for water level monitoring.

***********
CHESTER-X0C
***********

This module adds the possibility to connect up to 4 external analog/digital signals (maximum voltage up to 28 VDC).

**********
CHESTER-X1
**********

This module adds the 1-Wire interface. It can be used to connect external digital thermometer or HARDWARIO Soil Sensor.

.. list-table:: CHESTER-X1 pinout
   :widths: 10 10 80
   :header-rows: 1

   * - Terminal
     - Signal
     - Description
   * - x1
     - +V
     - Auxiliary positive battery voltage terminal
   * - x2
     - GND
     - System ground
   * - x3
     - VOUT
     - Positive power terminal for 1-Wire peripheral
   * - x4
     - DQ
     - Data signal 1-Wire peripheral
   * - x5
     - DQ
     - Data signal 1-Wire peripheral
   * - x6
     - VOUT
     - Positive power terminal for 1-Wire peripheral
   * - x7
     - GND
     - System ground
   * - x8
     - +V
     - Auxiliary positive battery voltage terminal

.. image:: _static/chester-x1.png
   :width: 300
   :alt: CHESTER-X1

***********
CHESTER-X2A
***********

This module adds the 3 V TTL/CMOS UART interface.

.. list-table:: CHESTER-X2A pinout
   :widths: 10 10 80
   :header-rows: 1

   * - Terminal
     - Signal
     - Description
   * - x1
     - GND
     - System ground
   * - x2
     - VDD
     - 3 V power
   * - x3
     - RX
     - Serial data in
   * - x4
     - TX
     - Serial data out
   * - x5
     - EN
     - Peripheral data alert
   * - x6
     - VDD
     - 3 V power
   * - x7
     - GND
     - System ground
   * - x8
     - +V
     - Auxiliary positive battery voltage terminal

.. image:: _static/chester-x2a.png
   :width: 300
   :alt: CHESTER-X2A

***********
CHESTER-X2B
***********

This module adds the RS-485 interface. For example, this can be used to interface Modbus peripherals.

.. list-table:: CHESTER-X2B pinout
   :widths: 10 10 80
   :header-rows: 1

   * - Terminal
     - Signal
     - Description
   * - x6
     - B
     - RS-485 signal B
   * - x7
     - A
     - RS-485 signal A
   * - x8
     - GND
     - System ground

.. image:: _static/chester-x2b.png
   :width: 300
   :alt: CHESTER-X2B

***********
CHESTER-X3
***********

This module adds the possibility to connect Pt1000 RTD thermometers in 4-wire (high-accurace) mode.

**********
CHESTER-X4
**********

This module adds the ability to power CHESTER from the external DC power supply. It integrates ultra-low-power DC/DC controller altogether with the ability to measure the input line voltage. Also, this module can measure 4-20 mA current loop input and implements 1-Wire master (the same functionality as CHESTER-X1).

The operating input voltage ranges from 5 VDC to 28 V DC.

.. list-table:: CHESTER-X4 pinout
   :widths: 10 10 80
   :header-rows: 1

   * - Terminal
     - Signal
     - Description
   * - x1
     - SOURCE
     - Positive power terminal for current loop sensor
   * - x2
     - SINK
     - Negative power terminal for current loop sensor
   * - x3
     - GND
     - System ground
   * - x4
     - VOUT
     - Positive power terminal for 1-Wire peripheral
   * - x5
     - DQ
     - Data signal 1-Wire peripheral
   * - x6
     - GND
     - System ground
   * - x7
     - VIN
     - Positive input rail (voltage range 4-28 VDC)
   * - x8
     - GND
     - System ground

.. image:: _static/chester-x4.png
   :width: 300
   :alt: CHESTER-X4

**********
CHESTER-X5
**********

This module adds the ability to measure external voltage in the range from -30 V to +30 V with the resolution of +/- 30 mV.

.. list-table:: CHESTER-X5 pinout
   :widths: 10 10 80
   :header-rows: 1

   * - Terminal
     - Signal
     - Description
   * - x7
     - GND
     - System ground
   * - x8
     - +VIN
     - Measured voltage -30 V to +30 V

.. image:: _static/chester-x5.png
   :width: 300
   :alt: CHESTER-X5
