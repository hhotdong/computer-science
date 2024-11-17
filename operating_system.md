Operating system(OS) overview

- OS is a software that...
- manages a computer's hardware, e.g. CPU, memory, I/O devices etc..
- controls the hardware and coordinates its use among the various application programs for the various users.
- provides a basis for application programs and acts as an intermediary between the computer user and the computer hardware.
- provides the means for proper use of the resources in the operation of the computer system, i.e., it simply provides an environment within which other programs can do useful work.

- In system view, OS is a...
- resource allocator which decides how to allocate resources like CPU time, memory space, storage space, I/O devices, to specific programs and users so that it can operate the computer system efficiently and fairly.
- control program which manages the execution of user programs to prevent errors and improper use of the computer. It is especially concerned with the operation and control of I/O devices. Since bare hardware alone is not particularly easy to use, application programs are developed. These programs require certain common operations, such as those controlling the I/O devices. The common functions of controlling and allocating resources are then brought together into one piece of software: the operating system.

- OS includes the always running kernel, middleware frameworks that ease application development and provide features, and system programs that aid in managing the system while it is running.

A modern general-purpose computer system consists of one or more CPUs and a number of device controllers connected through a common bus that provides access between components and shared memory. Each device controller is in charge of a specific type of device(for example, a disk drive, audio device, or graphics display). A device controller maintains some local buffer storage and a set of special-purpose registers. The device controller is responsible for moving the data between the peripheral devices that it controls and its local buffer storage.

Typically, operating systems have a device driver for each device controller. This device driver understands the device controller and provides the rest of the operating system with a uniform interface to the device. The CPU and the device controllers can execute in parallel, competing for memory cycles. To ensure orderly access to the shared memory, a memory controller synchronizes access to the memory.

### References

- Abraham Silberschatz, Peter Baer Galvin, Greg Gagne(2019), *Operating System Concepts, asia edition*, Wiley