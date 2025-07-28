### Q1. Why busy box?
> it's a tool to generate your own customized, memory friendly file system.
> it doesn't generate indiviual linux commmands binaries, there is only one executable binary that's called **busybox** which implements   all the required linux commands which you can select via the configuration tool.

### Q2. How to generate rfs using bus box?
> make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- defconfig
> make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- menuconfig
> make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- CONFIG_PREFIX=<install_path> install
 
