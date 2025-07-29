### Docs required
> 1. TRM (Technical reference manual)  
> 2. SRM (System reference manual)

### GPIO Highlights from TRM
> There are 4 GPIO modules provided in the SoC  
> Each module supports 32 GPIO pins  

### How to know the exposed pins on BBB?
> via SRM, go to expansion header section.  
> there two header and each one descripes 46 GPIO pins.

### Explain the expansion header?
| PIN | PROC | NAME | MODE0 | MODE1 | MODE2 | MODE3 | MODE4 | MODE5 | MODE6 | MODE7 |
| --- | ---- | ---- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| PIN no. of the expansion header | Pin name on the SoC in data sheet | Default mode of operation of this PIN | MODE0 | MODE1 | MODE2 | MODE3 | MODE4 | MODE5 | MODE6 | MODE7: indicates the GPIO port number and pin number |


### Remark: 
> All PINs behave as GPIO if they are configured to be MODE7  
> On the expansion header p8 you can get 44 gpios (46 - 2)  
> On the expansion header p9 you can get 23  
> Total gpios available on the bbb expansion header = 67

### How the the device files of the GPIO pins are presented and where?
> go to /sys/class/gpio  
> gpioX, X is the pin number ... so how to deduce the port number?!

### how to deduce the port number?
> example: MODE7 = gpio1 [6]
> sol: gpio1 [6] => 1*32 + 6 = 38 ===> GPIO38

### How to configure the pin mode between MODE0 to MODE7?
> go to TRM: Control module section   
> at pad(pin) configuration registers are present at offset 800h of he **control module engine**   
> BASE_ADDRESS = 0x44E1_0000 (deduce it from the memory map and check the start address of the control module engine registers)  
> BASE_ADDRESS (of control module registers) 0x44E1_0000 + 800h; pad configuration registers Starts at that location.  
> based upon the following table **<conf_<module>_<pin> Register Field Descriptions>** you can configure the pad (pin).

<img width="899" height="408" alt="image" src="https://github.com/user-attachments/assets/17eddd09-6110-4b56-b1ec-ce25dbf815ee" />

### How to check the current GPIO pins configurations?
> cat sys/kernel/debug/pinctrl/44e10800.pinmux-pinctrl-single/pins  
> Remark: make a map between the PIN numbering as presented from kernel-debug and from the SRM expansion header  


### How to control the GPIO pins?
> go to /sys/class/gpio

### How to create a device file for an un-existed gpio pin?
> echo <pin-number> > export

### How to play with any of the USR-LEDs?
> got to /sys/class/leds/usrX  
> cat trigger ==> That would show all the arguments that the device file can operate at
> echo "none" > trigger   ==> That would turn off the LEDx
