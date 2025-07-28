## uEnv.txt file:
> it's nothing but collections of various env variables which are initialized to number of uboot commands and automating the command execution. 

### Q1. How to access the interactive mode of uboot?
> During the boot of the BBB hit **the space bar** during the first 5 sec.

### Q2. How to list all of uboot commands?
> cmd $ help: lists all of the supported commands existed in the currently running uboot version.

### Q3. How to know how to use a cmd?
> run $ hepl <cmd>

### Q4. How to list all of the environmental variables?
> run $ printenv  
> hint: there are 2 types of them, standard/default env. variables and user defined env. variables.

### Q5. What is the usage of the user defined env. variables?
> Overriding changing the behavior of the uboot.

### Q6. How to create a new env variable and assign a value to it?
> $ setenv serverip 192.168.1.2  
> hint: you can store one or multible uboot command in a variable

### Q7. How to execute a command?
> $ run <cmd> or run <env_variable>  
> hint: in case of the env_variable holds a cmd of series of commands

### Q8. How to print out a message in the consol?
> echo"Write a message"

### Q9. How to transfer file (uEnv.txt) from your native machine to the boardd during the uboot phase?
> you can use one of the following protocols (i.e. xmodem, ymodem, zmodem)  
> after that import the uEnv.txt from memory by runninng this command ... $ env import -t <memory_address> <sizeInBytes>  
> remark: always leave a new line at the end of the file  

### Q10. List importand boot commands?
> boot: boot default, i.e., run 'bootcmd'
> bootm: boot from memory
> bootp: oot image via network using BOOTP/TFTP protocol
> bootz: boot Linux zImage image from memory

### 
``` uboot
# Step 1) Load the kernel image into DDRAM
# load from SD-Card from its file system of partition one the kernel image 'uImage' into the DDRAM at location 0x82000000
$ load mmc 0:1 0x82000000 uImage

# Step 2) Load DDB into DDRAM
$ load mmc 0:1 0x88000000 am335x-boneblack.dtb

# Step 3) Pass Boot Arguments to configure the kernel at boot
# bootargs: it's a standard env. variable by uboot
# 1. log out its traces to ttyO0
# 2. tell the kernel where should the rootfs located (i.e. sd-card, eMMC, UART or TFTP)
$ setenv bootargs consol=ttyO0,115200 root=/dev/mmcblk0p2 rw 

# Step 4) Boot application image stored in memory and the DTB
$ bootm 0x82000000 - 0x88000000
```

### Let's write a simple uEnv.txt
```uboot
serverip=192.168.1.2
targetip=192.168.27.1
setenv bootargs consol=ttyO0,115200 root=/dev/mmcblk0p2 rw
bootcmd=echo"******Booting from Memory*******"; load mmc 0:1 0x82000000 uImage; load mmc 0:1 0x88000000 am335x-boneblack.dtb; bootm 0x82000000 - 0x88000000;

```
