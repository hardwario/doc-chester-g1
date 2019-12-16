###################
Backend Integration
###################

The device communicates over the network to a so-called FLOT server.

.. note::

   The abbreviation FLOT stands for the **F**\ orward **L**\ ine of **O**\ wn **T**\ roops - a term used by the U.S. Department of Defense. In the context of HARDWARIO cloud infrastructure, it reflects the closest server component to the devices.

The FLOT server parses the incoming size-optimized binary message and produces a JSON message which is further passed to the incoming queue.

*******************
JSON Output Example
*******************

.. code-block:: json

   {
     "time": 1562702223,
     "data": {
       "frame": {
         "sequence": 8,
         "protocol": 1
       },
       "device": {
         "profile": "CHESTER",
         "hardware": null,
         "firmware": null
       },
       "state": {
         "uptime": 502,
         "tracking": false
       },
       "event": {
         "boot": false,
         "tilt": false,
         "button": false
       },
       "battery": {
         "voltage": 3.449
       },
       "tracking": {
         "time": 1562702029,
         "latitude": 507835072,
         "longitude": 141535392
       },
       "network": {
         "imei": 0,
         "imsi": 901288001061677,
         "nuestats": {
           "signal_power": -408,
           "total_power": -342,
           "tx_power": -190,
           "tx_time": 1644,
           "rx_time": 32088,
           "cell_id": 714016,
           "ecl": 0,
           "snr": 261,
           "earfcn": 6447,
           "pci": 135,
           "rsrq": -108
         }
       }
     }
   }

..
  TODO: Provide more complete JSON example
