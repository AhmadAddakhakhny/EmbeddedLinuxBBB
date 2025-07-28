### Beaglebone Linux kernel repo
> https://github.com/beagleboard/linux/tree/v5.10.168-ti-rt-r76#

### What files directories to care about in linux-src-tree?
> ##### Arch dependent
> 1. Board file: i.e.  /linux/arch/arm/mach-omap2/board-generic.c  
> 2. machine (SOC) shared common code: i.e. /linux/drivers
> 3. ARM CPU shared common code
> ##### Arch independent
> 1. Linux kernel shared common code
