What is mega1284duino?
--------

Mega1284duino is an effort to create a well maintained unified hardware profile for ATMega1284 for Arduino IDE.
There are many ATMega1284 or ATMega644 based projects like Sanguino, Bobuino, Calunium, Goldilocks.
They all have done a great work, but all have some issues. I compiled the best of all into this library to unite them all.
If you are new, this is your ultimate resource for building your own Arduino compatible ATMega1284 board.
Mega1284duino is no physical board you can buy, rather it's the starting point you build your own 
Arduino compatible board from that actually works.


What is ATMega1284?
--------

ATMega1284 is 8 bit microcontroller from Atmel very similar to ATMega328 commonly used in Arduino
It has:
		16k RAM												(ATMega328 has only 2k)
		128k Flash for your sketch		(ATMega328 has only 32k)
		4k EEPROM											(ATMega328 has only 1k)
		2 UARTS												(ATMega328 has only 1)
		4 timers											(ATMega328 has only 3)
		8 PWM													(ATMega328 has only 6)
		23 digital pins								(ATMega328 has only 13)

You'll get all of this just for double the price of ATMega328


Pinout
--------

Mega1284duino pinout is based on Goldilocks and is as much compatible with original Arduino pinout as possible.
You get extra 10 pins you are encouraged to use for your extra on board appliances


Bootloader
--------

I created a simple to use makefile and compiled a set of bootloaders for different 
frequencies and a baud rates you can use with FTDI cable.
Board definition file is using full swing oscillator setting to mitigate the issue of 
reseting the microcontroller (affects DIP package only) because of crosstalk between XTAL and UART


Arduino core
--------

The core library is based on the standard Arduino core library, which already supports ATMega1284 to some extend.
I made a few improvements (time related functions to support 24Mhz, 20Mhz, 12 Mhz crystals and other improvements) 
that I hope will find their way to the official Arduino library


How to use it?
--------

Just clone this repo into your arduino hardware directory and restart the Arduino IDE.


References
--------

http://www.ot-hobbies.com/resource/ard-1284.htm


Feedback
--------

Feedback and pull requests are appreciated.
