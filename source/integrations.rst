################
Cloud integrations
################

Via HARDWARIO Cloud you can integrate your device with several services and platforms

***************
Blynk IoT Platform
***************

Blynk makes easy to build mobile IoT app. Follow these simple steps to integrate CHESTER with Blynk via HARDWARIO Cloud:

1. Download Blynk App from `App Store`_ or `Google Play`_ and create new project.
2. Add widgets to the application and assing virtual PINs for every metric you want to visualise.
3. Go to HARDWARIO Cloud and create or select the group that your device is part of.

.. note::

   The Blynk API do not support sending multiple values for different PINs in one callback. 

4. Now you have to create a unique callback for all your virtual PINs. Use these instructions:

  a. Method 
  
  ::

    PUT
  
  b. URL Address

  ::

    http://blynk-cloud.com/<auth_token>/update/V<number>

  Replace <auth_token> by your generated token from Blynk and <number> with number of your virtual PIN.

  c. Payload

  ::

    [
      <<value>>
    ]

  Instead of <<value>> use extracted value from original JSON message. For example: 

  ::

    [
      data.sensor.hygrometer.temperature
    ]

.. _App Store: https://apps.apple.com/us/app/blynk-iot-for-arduino-esp32/id808760481

.. _Google Play: https://play.google.com/store/apps/details?id=cc.blynk&hl=en 