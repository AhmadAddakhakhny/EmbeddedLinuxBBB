### Q1. In nutshell RaspberryPi vs Beaglebone black?
> Rasp-pi: Faster CPU, more RAM, better GPU
> BBB: Better for real-time control contains (2x PRUs), idustrial I/O, and analog interfacing

### Q2. What is Programmable Real-Time Unit AKA. **PRU**?
> hey are special microcontrollers (like tiny CPUs) inside the TI Sitara SoC (used in BeagleBone Black) that run independently from the main ARM processor.
> 2 PRUs in BeagleBone Black (in the AM335x chip)
> Each PRU is a 32-bit RISC processor running at 200 MHz
> Deterministic timing – responds to I/O events with precise timing, unlike a Linux user-space app
> Has direct access to GPIO – can read/write pins at high speeds
> Can run real-time routines without being interrupted by the main Linux OS

### Q3. What software should be used on linux PCs to monitor serial communication and why to do so?
> SW tool: minicom .. Remark: Adjust its settings  to read the proper device file of the (USB-TTL)
> Reason: get direct access of the Linux consol (UART0), instead of using a display.
> This lets you: login to the terminal, debug boot issues, view kernel logs(u-boot or Linux), Fix misconfigured network settings

| Reason to Use USB-TTL Adapter        | Why It's Useful                                 |
| ------------------------------------ | ----------------------------------------------- |
| Serial console access                | Debug boot, configure system without display    |
| Early-stage debugging (U-Boot, logs) | See output before OS boots                      |
| No Ethernet or USB access            | Alternative way to control the board            |
| Works on headless systems            | Perfect for embedded/IoT devices                |
| Stable and always available          | Unlike SSH, serial works even when OS is broken |

### Q4. What is SoC?
> It's a system on chip composed of lots of peripherals and their controllers (if required) and memory
> AM3358: it's a SoC provided by TI
> TRM: Technical reference manual -> shows all the details of the functional blocks of the SoC

### Q5. What is the heart of an SoC AM3358?
> MPU: micro processing unit and it's ARM Cortex-A8 up to 1GBH 32 RISC
