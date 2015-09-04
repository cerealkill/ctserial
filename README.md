# jpnevulator.py

This software is implementation of the serial sniffing tool [jpnevulator][] in Python.
It's aim is to emulate the command line interface and the output of the original tool as much as possible:

    $ jpnevulator --ascii --timing-print \
      --tty /dev/ttyS0:SB9600d \
      --tty "/dev/ttyUSB0:Motorola MTM800" \
      --read
    2015-08-30 13:23:49.461075: SB9600d
    00 00 05 3B 0D 00 00 05                         ...;....
    2015-08-30 13:23:49.461113: Motorola MTM800
    00 05 3B 0D 00 00 05 3B 0D                      ..;....;.
    2015-08-30 13:23:49.473074: SB9600d
    3B 0D 00 00 05 3B 0D                            ;....;.
    2015-08-30 13:23:49.473105: Motorola MTM800
    00 12 05 06 39 00 12 05 06 39 1F 00 22 80 00 0E ....9....9.."...
    $ 

### Additional features

One feature that is available in this Python implementation (and missing in the original tool) is setting the baudrates.
This is supported by adding them to the tty device name separated by an `@`:

    jpnevulator --ascii --timing-print \
      --tty /dev/ttyUSB0@9600:SENDING \
      --tty /dev/ttyUSB1@9600:RECEIVING \
      --read

### Platform Independence

I had problems getting the original jpnevulator to work on Mac OS X. Thus, I wrote this platform independent replacement:
Python and the [PySerial][] package this software depends on are availabe for all major operating systems.

### Author

* Philipp Klaus  
  <philipp.l.klaus@web.de>

[jpnevulator]: http://jpnevulator.snarl.nl/
[PySerial]: http://pyserial.sourceforge.net/