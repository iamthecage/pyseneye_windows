pyseneye
========

|Build Status| |Coverage Status|

Quick Windows fork of PySeneye.  Tested only on my Windows 10 PC.  Will pull Seneye readings in Windows, as well as any virtual machines you pass the usb device to.

A module for working with the Seneye range of aquarium and pond sensors.
Support is provided for the HID/USB driver for the device although it is
intended to add support for their API later.

When using this, readings will not be synced to the Seneye.me cloud
service. This module is in no way endorsed by Seneye and you use it at
your own risk.

Generated documentation can be found
`here <http://pyseneye.readthedocs.io/en/latest/>`__

Quickstart
----------
Make sure Seneye Connect App is shutdown and unplug the Seneye from your PC
Download both Seneye_SUD_v_2.0.16.cat and Seneye_SUD_v_2.0.16.inf
Right Click on Seneye_SUD_v_2.0.16.inf and select Install
(you will need to uninstall this device in Device Mangager and delete the files when prompted to use the Seneye Connect App)
Reinsert the Seneye USB
You should have a Seneye device in Device Manager now listed under "libusb-win32 devices"

Install pyseneye using ``pip``: ``$ pip install pyseneye_windows``. Once that is
complete you can import the SUDevice class and connect to your device.

.. code:: python

    >>> from pyseneye_windows.sud import SUDevice, Action
    >>> d = SUDevice()

Once the class is initialised you can put the Seneye into interactive
mode and then retrieve sensor readings.

.. code:: python

    >>> d.action(Action.ENTER_INTERACTIVE_MODE)
    >>> s = d.action(Action.SENSOR_READING)
    >>> s.ph
    8.16
    >>> s.nh3
    0.007
    >>> s.temperature
    25.125
    >>> d.action(Action.LEAVE_INTERACTIVE_MODE)
    >>> d.close()

You need access to the USB device, so these calls may require elevated
privileges.

Issues & Questions
------------------

If you have any issues, or questions, please feel free to contact me, or
open an issue on GitHub

.. |Build Status| image:: https://travis-ci.org/mcclown/pyseneye.svg?branch=master
   :target: https://travis-ci.org/mcclown/pyseneye
.. |Coverage Status| image:: https://coveralls.io/repos/mcclown/pyseneye/badge.svg?branch=master&service=github
   :target: https://coveralls.io/github/mcclown/pyseneye?branch=master
