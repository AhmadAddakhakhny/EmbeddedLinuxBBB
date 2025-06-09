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
