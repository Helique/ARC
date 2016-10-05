# ARC
This Project is a test of the communication between Raspberry PI and the Arduino Uno using I2C.
## Required Hardware
1. Raspberry Pi 2 ( or better)
2. Arduino Uno with USB cable
3. Breadboard
4. Wires
5. Raspberry PI 2 GPIO to breadboard
6. USB power for raspberry pi.
7. Monitor/Tv for raspberry pi
8. A development computer to load arduino code/ make raspberry pi OS images.
9. HDMI cable
10. Ethernet for the raspberry pi will make your life easier, or the built-in wifi in the rpi 3 "should" be easy enough.

## Raspberry PI
Pinout:
http://www.raspberrypi-spy.co.uk/wp-content/uploads/2012/06/Raspberry-Pi-GPIO-Layout-Model-B-Plus-rotated-2700x900.png

The raspberry pi is a small computer that runs a non-real time operating system. This means that syncronization of the stepper motors cannot be garenteed and will fluctuate. In order to handle this, the timing is enforced by the Arduino. Data will be buffered on some level, so that the jitters of the Raspberry pi do not cause pauses or bursts in the operation of the motors. 

The operating system of choice is Raspbian, specifically the lite version as a gui is not needed. All code can either be typed into the terminal, or transfered to the pi using things such as git or rsync.

After you get Raspbian-lite installed on a micro sd card and the rpi boots from it, you need to expand the file system before installing anything else. If you don't do this, you will run out of storage space, and you will need to delete files in order to delete programs in order to expand the file system.



## Arduino
Pinout:https://camo.githubusercontent.com/0174ab1436903eb06dfea280a83c389460637054/68747470733a2f2f7261776769746875622e636f6d2f426f756e692f41726475696e6f2d50696e6f75742f6d61737465722f41726475696e6f253230556e6f253230523325323050696e6f75742e706e67

Arduino is an atmel microprocessor that is easily programmed at a higher level thanks to the abstractions provided by the Arduino language. The processor is single threaded and can be interupted by timers which make it a good candidate for handling the syncronization of Motors.

To work on the arduino, the Arduino IDE must be installed. Once this is done, you can find the "sketchbook" folder for your development computer (not the rpi). In this there is a libraries folder, and installing new libraries is as easy as dropping an unzipped library folder into this folder. When the Arduino IDE is restarted, your libraries will be there. 

## I2C

I2C is a way for the raspberry pi and Arduino to talk to each other. It allows a master to talk to many slave devices. Each slave has a unique address, that the master can talk to.  For this project I had a hard time sending a lot of data to the arduino at once, and need to look into ways to make the connection very reliable and fast. 

Hello World Tutorial: https://blog.retep.org/2014/02/15/connecting-an-arduino-to-a-raspberry-pi-using-i2c/

## SPI

SPI is another way for the raspberry pi and arduino to talk to each other. This one has sepeate wires for data in and data out. The master decides which device to talk to using a seperate wire for each device. This is different from the addressing scheme of i2c. I also had problems getting this to be fast and reliable. I have heard similar things from Professor Brewer at UCSB that SPI is highly device dependent.

Hello World Tutorial: http://mitchtech.net/raspberry-pi-arduino-spi/
