.. _serial:

============
Serial ports
============
The MX-4 contains three serial ports which can be used to connect to other units. Full RS-232 with CTS/RTS, RS-232 RX/TX and RS-485.

The interal linux map to external connector::

    /dev/ttyHS1 ---> RS485
    /dev/ttyHS3 ---> RS232/CTS/RTS (RS232-1)
    /dev/ttyS1  ---> RS232 TX/RX (RS232-2)

