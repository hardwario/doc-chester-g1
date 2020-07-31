##################
Cloud Integrations
##################

Via HARDWARIO Cloud you can integrate your device with several services and platforms

******************
Blynk IoT Platform
******************


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

======================
CHESTER Clime example:
======================

Now we are going to make an example with CHESTER Clime.

1. Download Blynk App from `App Store`_ or `Google Play`_ and scan QR Code in next step to copy dashboard:

  .. image:: _static/integrations/blynk/blynk-app-scan.png
      :scale: 40 %

2. Now scan Dashboard QR Code:

  .. image:: _static/integrations/blynk/blynk-dashboard.png
      :scale: 80 %

  You should see following dashboard:

  .. image:: _static/integrations/blynk/blynk-app-chester-dashboard.png
      :scale: 40 %

3. Now open HARDWARIO Cloud and navigate to Group Callbacks in HARDWARIO Cloud:

  .. image:: _static/integrations/blynk/hardwario-cloud-managment.png
      :scale: 51 %

4. Select your Group callbacks with CHESTER Clime:

  .. image:: _static/integrations/blynk/hardwario-cloud-group-callbacks.png
      :scale: 51 %

  .. note::
      For now is need to have only one device in single Group.

5. Add temperature callback:

  For each quantity we will be setting special callback. For **temperature** name it Blynk temperature, method is **PUT**
  and URL address is ``http://blynk-cloud.com/<AUTH TOKEN>/update/V0``

  .. image:: _static/integrations/blynk/hardwario-cloud-callback-1.png
      :scale: 51 %

  .. note::
      For CHESTER dashboard you revieved **AUTH TOKEN** to account email.

  As payload put following code and click **SAVE CALLBACK**:

  ::

    [
    data.sensor.hygrometer.temperature
    ]

  .. image:: _static/integrations/blynk/hardwario-cloud-callback-2.png
      :scale: 51 %

6. Add left callback (humidity and orientation):

  Repeat previous chapter, but use following callbacks and payloads and replace ``<AUTH TOKEN>`` with your own:

    Humidity:

    +---------+---------------------------------------------------+
    | URL     | ``http://blynk-cloud.com/<AUTH TOKEN>/update/V1`` |
    +---------+---------------------------------------------------+
    | Payload | [                                                 |
    |         | data.sensor.hygrometer.humidity                   |
    |         | ]                                                 |
    +---------+---------------------------------------------------+

    Orientation:

    +---------+---------------------------------------------------+
    | URL     | ``http://blynk-cloud.com/<AUTH TOKEN>/update/V2`` |
    +---------+---------------------------------------------------+
    | Payload | [                                                 |
    |         | data.sensor.accelerometer.orientation             |
    |         | ]                                                 |
    +---------+---------------------------------------------------+

7. After a while, CHESTER will send data and you will se them in Blynk app:

  .. image:: _static/integrations/blynk/blynk-app-finish.png
      :scale: 40 %

.. _App Store: https://apps.apple.com/us/app/blynk-iot-for-arduino-esp32/id808760481

.. _Google Play: https://play.google.com/store/apps/details?id=cc.blynk&hl=en 