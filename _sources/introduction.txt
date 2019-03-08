.. _introduction:

============
Introduction
============

MX-4 is a scalable Linux platform targeting automotive environments. The family consists of more then 10 of the shelf products and we keep increasing the product range as we get feedback and requirements from our customers.

`Smörgåsbord <https://en.wikipedia.org/wiki/Sm%C3%B6rg%C3%A5sbord>`_ of features within the MX-4 product range:

* Onboard cellular device (GPR/EDGE/3G/LTE)
* WiFi
* Wired Ethernet
* Automotive communication interfaces
  
    * Controller Area Network (CAN)
    * Local Interconnect Network (LIN)
    * J1708
    * ISO9141

* Large amount of general purpose I/O

    * RS-232
    * RS-485
    * Digitial I/O
    * Analog I/O
    * USB Host/Device
    * Audio
    * Display (VGA/HDMI)

* Extensible storage (SD)
* Industrial temperature range
* Low power modes (SLEEP/DEEP-SLEEP)

This documentation is intended for developers using an MX-4 product and our goal is to "rocket launch" you application development.

Board Support Package
==============================

To support our rich list of hardware features we provide an professionally maintained, state of the art board support package (BSP).

The core components of the BSP are:

* Linux kernel (version depends on SoC)
* U-boot (2016.11)
* Yocto/OE-core integration (2.2/morty)

    * Binary package feeds (Ångström/Toradex)
    * gcc 6.2 
    * glibc 2.24
    * systemd 230

* Firmware update support, extensible to do OTA updates

We provide access to our build server where one can download nightly builds of the BSP. There is a also an possibility to create custom jobs on the server depending on customer requirements.

Resources
---------

Large portions of the BSP is provided as open-source and can be found on `github/hostmobility <https://github.com/hostmobility>`_. 

The parts that are considered closed source are only accessible by our customers and are required to fully utilize the devices. If you have an MX-4 device you probably are a customer and will get access to this part of the BSP together with your device.

