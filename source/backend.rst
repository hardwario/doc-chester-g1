###################
Backend Integration
###################

The device communicates over the network to a so-called FLOT server.

.. note::

   The abbreviation FLOT stands for the **F**\ orward **L**\ ine of **O**\ wn **T**\ roops - a term used by the U.S. Department of Defense. In the context of HARDWARIO cloud infrastructure, it reflects the closest server component to the devices.

The FLOT server parses the incoming size-optimized binary message and produces a JSON message which is further passed to the incoming queue.
