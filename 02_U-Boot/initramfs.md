### Q1. What is initramfs ?
> The word "initramfs" is made up of three words "initial" "RAM based" "file system".  
> initramfs is a compressed cpio archive embedded or loaded by the bootloader.  
> It contains a minimal root filesystem (often with BusyBox) and an init script.  
> It is unpacked into RAM and mounted as / before the actual root filesystem.  

### Q2. Does that mean usage of initramfs is compulsory? Used everywhere, every time ?
> No, not necessarily. Using initramfs is optional.

### Q3. why do we need initramfs ?
| Function                    | Purpose                                      |
| --------------------------- | -------------------------------------------- |
| Early driver/module loading | Load disk/NIC/filesystem modules before root |
| Hardware initialization     | Handle special devices like NVMe, USB boot   |
| Root filesystem preparation | Decrypt or assemble RAID/LVM                 |
| System recovery/debugging   | Provide shell if root mount fails            |
| Configuration flexibility   | Select rootfs dynamically (e.g. USB vs SD)   |

### Q4. List Use Cases
> Booting BeagleBone Black from SD card with custom drivers  
> Booting Raspberry Pi with encrypted filesystem  
> Embedded Linux systems using BusyBox with minimal rootfs

### Q5. How to keep initramfs in to RAM?
> 1. You can make initramfs “built in” in to the Linux Kernel during compilation, so when the Linux starts booting , it will place the initramfs in the RAM and mounts as the initial root file system and continues.  
> 2. You can load the initramfs from some other sources in to the RAM of your board and tell the Linux Kernel about it (that is , at  what RAM address initramfs is present ) via the kernel boot arguments.

### Q6. How to generate the innitramfs ?
> Download the tiny filesystem from TI SDK "am335x_tiny_filesystem", extract the zip file and run the following commmands
```bash
apt-get install u-boot-tools
find . | cpio -H newc -o > ../initramfs.cpio
cat ../initramfs.cpio | gzip > ../initramfs.gz
mkimage -A arm -O Linux -T ramdisk -C none -a 0x80800000 -n "Root Filesystem" -d ../initramfs.gz  ../initramfs  
```
