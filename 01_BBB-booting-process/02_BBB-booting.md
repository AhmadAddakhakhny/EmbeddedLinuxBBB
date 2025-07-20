### Q1. What do we need to successfully boot linux on BBB?
> 1. RBL: AKA. ROM Boot Loader - first stage bootloader runs out of ROM
> 2. SPL/MLO: Secondary stage bootloader / Memory loader runs out of internal SRAM
> 3. U-Boot: runs out of DDR 

### Q2. What are BeagleBone Board Boot Options?
> Briefly, there are 4 options
> 1. eMMC Boot
> 2. SD Boot
> 3. Serial Boot
> 3. USB Boot

### Q3. What is the purpose of RBL?
> mainly,
> 1. It's flashed on the SoC ROM by the silicaon provider and can't be over written
> 2. Checks the booting source list, and decide from what source to boot from
> 3. Setup the WDT expiration to be 3 mins to restart in case the SPL not found
> 4. for BBB: checks the SYSBOOT register and based on it sets the systems frequency and boot source
> 5. Loads the SPL
> Remark: for more info read about BBB-boot-process from **TRM**

### Q4. How RBL Loads the SPL?
> The RBL-SW checks the **image header** of the SPL which located in the eMMC/SD-Card
> and verifies two things, the start address (load address) of the SRAM wher the SPL should be fetched into, and the size of the SPL.
> if both information are valid, RBL starts loading the SPL into the SRAM
> Remark: ROM and SRAM are located inside the SoC.

### Q4. What is the purpose of SPL/MLO?
> 1. Performs UART consol initialization to print out the debug messages.
> 2. Reconfigure the PLL to the desired value
> 3. Copies the u-boot image into the DDR memory and passes the control to it.

### Q5. Can we avoid using MLO or SPL by making RBL directly loads the U-Boot into internal SRAM?
> In theory, it's possible but the SRAM has to be large enough to host the U-Boot
> and To do so with **BBB** the u-boot image has to be squeezed and be <128KB of size. (that isn't possible)

### Q6. Can we use RBL to load U-boot directly into DDR Memory of the board and skip using MLO or SPL?
> Mostlikely it's not a common practice amond the board providers.
> as the typical boards such **BBB** it's not possible, as ROM code won’t be having any idea about what kind of DDR RAM being used in the product to initialize it.

### Q8. What is the job/purpose of U-Boot?
> Used to load the linux kernel  
> Initialize some of the preipherals like I2C, NAND, FLASH, ETHERNET, UART, USB, MMC, etc. becasue it supports loading kernel from all these peripherals.  
> Load linux kernel image from various boot sources to the DDR memory of the board.  
> passing of boot arguments to the kernel  
> uboot looks for uimage, and **uimage** is composed of **64 Bytes uboot image header + zImage(ELF)**  

### Q9. What is the job of uEnv.txt?
> it's being used by the u-boot.  
> you can change the boot behaviour of the u-boot by using this file.  
> This file is being used to set som enviroment variables which drives the uboot according to your need.

