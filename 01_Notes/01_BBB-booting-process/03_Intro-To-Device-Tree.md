### Q1. What are the types of preipherals?
> self-dicoverable devices: it can send its information to the OS and be initialized (i.e. USB devices)    
> non self-discoverable devices:  it can't communicate with the OS (i.e. I2C, SPI). AKA. platform devices 

### Q2. Define platform devices?
> The on-board preipherals which connect to SPI, I2C, SDIO, Ethernet ...etc have no compatability to announce their existence on the board by themselves to the operating system. these preipherals are also called as "platform devices".  

### Q3. Why Device tree is introduced?
> The linux community wanted to cut off the dependancies of the platform device enumeration from the linux kernel, that is, hard coding of the platform device specific details into the linux kernel.

### Q4. What is device tree source file (DTS)?
> Instead of adding hard coded hardware details into the linux kernel board file, every board vendors has to come up with a file called DTS.

### Q5. What is device tree compiler (DTC)?
> It's a compiler used to compile DTS files to DTB files.

### Q6. What is device tree binary?
> It's a stream of bytes being read by the kernel to susbtitute the self-discovery for platform devices.  
> During the booting linux must know the address at which DTB is present in the RAM.
