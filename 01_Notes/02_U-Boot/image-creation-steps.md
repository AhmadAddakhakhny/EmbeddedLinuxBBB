``` Bash
********************************* Cross toolchain installation *********************************
# Step 1: Install arm cross toolchain for your host machine  
https://releases.linaro.org/components/toolchain/binaries/latest-5/arm-linux-gnueabihf/  
#Step 2: Export the path of cross compilation toolchain  

********************************* Cross compile uboot *********************************
# Step 1: clean the source directory
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- distclean

# Step 2: Generate a config file for BBB based upon the default configurations
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- am335x_evm_defconfig

# Step 3: [Optional] run menuconfig, if you want to do any settings other than the defaul ones.
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- menuconfig

# Step 4: Compile
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4

********************************* Cross compile linux kernel *********************************
# Step 1: clean the source directory
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- distclean

# Step 2: Generate a config file for BBB based upon the default configurations
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- omap2plus_defconfig

# Step 3: [Optional] run menuconfig, if you want to do any settings other than the defaul ones.
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- menuconfig

# Step 4: Compile kernel with static modules
# Generated images: /arm/boot/
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- uImage dtbs LOADADDR=0x80008000 -j4

# Step 5: Compile dynamic/loadable modules
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -j4 modules

# Step 6: Install the RFS
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf-  INSTALL_MOD_PATH=<path-of-the-RFS> modules_install
```
