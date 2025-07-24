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
> $ setenv serverip 192.168.27.1  
> hint: you can store one or multible uboot command in a variable

### Q7. How to execute a command?
> $ run <cmd> or run <env_variable>  
> hint: in case of the env_variable holds a cmd of series of commands

### How to print out a message in the consol?
> echo 

### List importand boot commands?
> boot:
> bootd:
> bootm:
> bootf:
> bootz:



### Hints:
