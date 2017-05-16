.. _digio:

===========
Digital I/O
===========

For digital I/O we utilize the `GPIO Sysfs interface for Userspace <https://www.kernel.org/doc/Documentation/gpio/sysfs.txt>`_.

To get a list available ports::

    $ cat /sys/kernel/debug/gpio | grep -i digital

Above command will produce a very long list of I/O ports and your device probably does not have hardware support for all of them. For details consult the technical manual of your specific device.

Read the value if a single digital input::

    $ cat /sys/class/gpio/gpio23/value

Write a value to a single digital output::

    $ echo 1 > /sys/class/gpio/gpio238/value

All digital inputs can generate an "event" on a specific change. The changes are "rising", "falling" or "both"

To setup an digital input to generate an event::

    $ echo rising > /sys/class/gpio/gpio23/edge

To listen for event you need to run `poll(2) <http://man7.org/linux/man-pages/man2/poll.2.html>`_ on the "value" file of that specific input. See `example application <https://github.com/hostmobility/file-poll>`_



