# Operating system

<details><summary>OS is a software that...</summary>
  
  - manages a computer's hardware, e.g. CPU, memory, I/O devices etc..
    
  - controls the hardware and coordinates its use among the various application programs for the various users.
    
  - provides a basis for application programs and acts as an intermediary between the computer user and the computer hardware.
    
  - provides the means for proper use of the resources in the operation of the computer system, i.e., it simply provides an environment within which other programs can do useful work.
    
</details>

<details><summary>In system view, OS is a...</summary>

  - <details><summary>resource allocator</summary>
    
    which decides how to allocate resources like CPU time, memory space, storage space, I/O devices, to specific programs and users so that it can operate the computer system efficiently and fairly.

    </details>

  - <details><summary>control program</summary>
    
    which manages the execution of user programs to prevent errors and improper use of the computer. It is especially concerned with the operation and control of I/O devices. Since bare hardware alone is not particularly easy to use, application programs are developed. These programs require certain common operations, such as those controlling the I/O devices. The common functions of controlling and allocating resources are then brought together into one piece of software: the operating system.

    </details>

</details>

<details><summary>Computer system organization</summary>

  - OS includes the always running kernel, middleware frameworks that ease application development and provide features, and system programs that aid in managing the system while it is running.

  - A modern general-purpose computer system consists of one or more CPUs and a number of device controllers connected through a common bus that provides access between components and shared memory. Each device controller is in charge of a specific type of device(for example, a disk drive, audio device, or graphics display). A device controller maintains some local buffer storage and a set of special-purpose registers. The device controller is responsible for moving the data between the peripheral devices that it controls and its local buffer storage.

  - Typically, operating systems have a device driver for each device controller. This device driver understands the device controller and provides the rest of the operating system with a uniform interface to the device. The CPU and the device controllers can execute in parallel, competing for memory cycles. To ensure orderly access to the shared memory, a memory controller synchronizes access to the memory.

</details>

<details><summary>Interrupts</summary>

  - Consider a typical computer operation: a program performing I/O. To start an I/O operation, the device driver loads the appropriate registers in the device controller. The device controller, in turn, examines the contents of these registers to determine what action to take (such as "read a character from the keyboard"). The  controller starts the transfer of data from the device to its local buffer. Once the transfrer of data is complete, the device controller informs the deivce driver that it has finished its operation. The device driver then gives control to otehr parts of the operating system, possibly returning the data or a pointer to the data if the operation was a read. For other operations, the device driver returns status information such as "write completed successfully" or "device busy". But how does the controller inform the device driver that it has finished its operation? This is accomplished via an interrupt.

  - Hardware may trigger an interrupt at any time by sending a signal to the CPU, usually by way of the system bus. (There may be many buses within a computer system, but the system bus is the main communications path between the major components.) Interrupts are used for many other purposes as well and are a key part of how operating systems and hardware interact.

  - When the CPU is interrupted, it stops what it is doing and immediately transfers execution to a fixed location. The fixed location usually contains the starting address where the service routine for the interrupt is located. The interrupt service routine executes; on completion, the CPU resumes the interrupted computation.

  - INterrupt are an important part of a computer architecture. Each computer design has its own interrupt mechanism, but several functions are common. The interrupt must transfer control to the appropriate interrupt service routine. The straightforward method for managing this transfer would be to invoke a generic routine to examine the interrupt information. The routine, in turn, would call the interrupt-specific handler. However, interrupt must be handled quickly, as the occur very frequently. A table of pointers to interrupt routines can be used instead to provide the necessary speed. The interrupt routine is called indirectly through the table, with no intermediate routine needed. Generally, the table of pointers is stored in low memory (the first hundred or so locations). These locations hold the addresses of the interrupt service routines for the various devices. This array, or interrupt vector, of addresses is then indexed by a unique number, given with the interrupt request, to provide the address of the interrupt service routine for the interrupting device. Operating systems as different as Windows an UNIX dispatch interrupts in this manner.

  - The interrupt architecture must also save the state information of whatever was interrupted, so that it can restore this information after servicing the interrupt. If the interrupt routine needs to modify the processor state, for instance by modifying register values, it must explicitly save the current state and then restore that state before returning. After the interrupt is serviced, the saved return address is loaded into the program counter, and the interrupted computation resumes as though the interrupt had not occurred.

  - <details><summary>Interrupts</summary>

    - The basic interrupt mechanism works as follows. The CPU hardware has a wire called the interrupt-request line that the CPU senses after executing every instruction. When the CPU detects that a controller has asserted a signal on the interrujpt-request line, it reads the interrupt number and jumps to the interrupt-handler routine by using that interrupt number as an index into the interrupt vector. It then starts execution at the address associated with that index. The interrupt handler saves any state it will be changing during its operation, determines the cause of the interrupt, performs the necessary processing, performs a state restore, and executes a return_from_)interrupt instruction to return the CPU to the execution state prior to the interrupt. We say that the device controller raises an interrupt by asserting as signal on the interrupt request line, the CPU catched the interrupt and dispatches it to the interrupt handler, and the handler clears the interrupt by servicing the device.
   
    - The basic interrupt mechanism just described enables the CPU to respond to an asynchronous event, as when a device controller becoumes ready for service. In a modern operating system, however, we need more sophisticated interrupt-handling features.
      - We need the ability to defer interrupt handling during critical processing.
      - We need an efficient way to dispatch to the proper interrupt handler for a device.
      - We need multilevel interrupts, so that the operating system can distinguish between high- and low-priority interrupts and can respond with the appropriate degree of urgency.
    In modern computer hardware, these three features are provided by the CPU and the interrupt-controller hardware.

  - Most CPUs have two interrupt request lines. One is the nonmaskable interrupt, which is reserved for events such as unrecoverable memory errors. The second interrupt line is maskable: it can be turned off by the CPU before the execution of critical instruction sequences that must not be interrupted. The maskable interrupt is used by device controllers to request service.

  - Recall that the purpose of a vectored interrupt mechanism is to reduce the need for a single interrupt handler to search all possible sources of interrupts to determine which one needs service. In practice, however, computers have more devices (and, hence, interrupt handlers) than they have address elements in the interrupt vector. A common way to solve this problem is to use interrupt chaining, in which each element in the interrupt vector points to the head of a list of interrupt handlers. When an interrupt is raised, the handlers on the corresponding list are called one by one, until one is found that can service the request. This structure is a compromise between the overhead of a huge interrupt table and the inefficiency of dispatching to a single interrupt handler.

  - The interrupt mechanism also implements a system of interrupt priority levels. These levels enable the CPU to defer the handling of low-priority interrupts without masking all interrupts and makes it possible for a high-priority interrupt to preempt the execution of a low-priority interrupt.
  
  - In summary, interrupts are used throughout modern operating systems to handle asynchronous events (and for other purposes). Device controllers and hardware faults raise interrupts. To enable the most urgent work to be done first, modern computers use a system of interrupt priorities. Because interrups are used so heavily fore time-sensitive processing, efficient interrupt handling is required for good system performance.

    </details>

</details>

### References

- Abraham Silberschatz, Peter Baer Galvin, Greg Gagne(2019), *Operating System Concepts, asia edition*, Wiley
