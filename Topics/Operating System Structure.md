OS structure is the specification of the kernel of the system
-  **Simple Structure**
	They do not have well defines structures, usually small and limited, e.g. MS-DOS, applications have direct acces to the I/O devices. There is no hardware protection or dual mode operation

- **Monolithic Structure**
	Initial Unix systems used the structure, they were divided into the kernel and system programs, the kernel takes care of the interface with the I/O devices, it is also responsible for file systems, memory management, and CPU scheduling since all the features are done by one module its monolithic.

  - **Layered Approach**
	The operating system consists of multiple layers which define each layer of the computing device, such as the lowest level is for hardware and highest layer is the the user interface, each layer can invoke each operation in a layer below it. This simple to build and debug but layer planning is difficult.![[Images/Pasted image 20230722185639.png]]

- **Microkernel Structure**
	The kernel in the system is smaller than in monolithic and removes and splits all the non-essential tasks to other components. The kernel only takes care of minimal process and memory management as well as communication with the hardware. This makes is easier to upgrade and isolate increasing security and reliability

- **Modular Structure** 
	The kernel implements loadable modules which separates the utility of the kernel which makes it easier to develop and extend the system, this can lead to smaller and faster systems with more security, by having isolation between the different parts of the system.