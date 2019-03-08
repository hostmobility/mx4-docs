.. _can:

=============================
Controller Area Network (CAN)
=============================
All MX-4 boards are equipped with CAN controllers. The `SocketCAN <https://www.kernel.org/doc/Documentation/networking/can.txt>`_ application interfaces is used to access hardware, this is the standard interface now days to communicate with CAN hardware on Linux.

Configuration
-------------

The most common way to configure a CAN device is using the `iproute2i <https://wiki.linuxfoundation.org/networking/iproute2>`_ util.

List of supported switches::

    $ ip link set can0 type can help  
    Usage: ip link set DEVICE type can
            [ bitrate BITRATE [ sample-point SAMPLE-POINT] ] |
            [ tq TQ prop-seg PROP_SEG phase-seg1 PHASE-SEG1
              phase-seg2 PHASE-SEG2 [ sjw SJW ] ]

            [ dbitrate BITRATE [ dsample-point SAMPLE-POINT] ] |
            [ dtq TQ dprop-seg PROP_SEG dphase-seg1 PHASE-SEG1
              dphase-seg2 PHASE-SEG2 [ dsjw SJW ] ]

            [ loopback { on | off } ]
            [ listen-only { on | off } ]
            [ triple-sampling { on | off } ]
            [ one-shot { on | off } ]
            [ berr-reporting { on | off } ]
            [ fd { on | off } ]
            [ fd-non-iso { on | off } ]
            [ presume-ack { on | off } ]

            [ restart-ms TIME-MS ]
            [ restart ]

            Where: BITRATE  := { 1..1000000 }
                      SAMPLE-POINT  := { 0.000..0.999 }
                      TQ            := { NUMBER }
                      PROP-SEG      := { 1..8 }
                      PHASE-SEG1    := { 1..8 }
                      PHASE-SEG2    := { 1..8 }
                      SJW           := { 1..4 }
                      RESTART-MS    := { 0 | NUMBER }

So to simply configure bitrate of one specific CAN controller::

    $ ifconfig can0 down
    $ ip link set can0 type can bitrate 250000
    $ ifconfig can0 up

To query a device for its current configuration::

    $ ip -d link show can0

To query a device for statistics::

    $ ip -s link show can0

Utilities
---------

You should also get familiar with `can-utils <https://github.com/linux-can/can-utils>`_. This is a colllection of tools that are great to debug CAN networks, applications and should be used as a source of insperation if you are to write your own application that interacts with an CAN network.

Dump all incoming data::

    $ candump -l any,0:0,#FFFFFFFF    (log error frames and also all data frames)

Send a single CAN frame::

    $ cansend can0 123#DEADBEEF
