# Operating Systems
An operating system is program that acts as the interface between the user and the computer and controls the execution of all kinds of programs.

## Functions of an Operating System
-  **Memory Management**
	The Operating system is responsible for management of the main memory, it keeps track of who and what is in memory at any given moment and decides how much and if it can allocate memory to a new process. The OS also deals with allocation and deallocation of the memory.

-  **Processor Management**
	The OS determines process scheduling, it keeps track of ongoing and waiting processes, allocates CPU cycles to compute what the process wants and deallocate if the process is over.

-  **Device Management**
	Keeping track of all I/O devices and managing them and ensuring all of the hardware works properly is an important part of the operating system. Mainly is about communication between IO Devices. 

-  **File Management**
	The Operating system is responsible for organization of files into directories and makes use of the storage to easily access the data. The OS determines the permissions to each and every process and allows or denies the access to those files.

-  **Security and Protection**
	The Operating system makes use of techniques such as encryption and passwords to ensure data isolation and privacy of the data and prevents unauthorized access.

-  **Job Accounting**
	Keeping track of time and resources used by process and users.

-  **Error detecting aids**
	Helps in detecting errors in programs and keeps a log of all activities and creates dumps and provides debugging info too.

## [[Topics/Types of Operating Systems|Types of Operating Systems]]
#important 
-  **Batch Operating System**
-  **Multiprogrammed** 
-  **Multiprocessor System**
-  **Time Sharing System**
-  **Real Time System**
-  **Distributed Systems**

## Operating System Services
- User Interface
	The operating system proved the user with the interface which they can use to start or stop process and issue commands to the operating system, some of the interfaces includes:
	- GUI's (Graphical user interfaces) 
	- CLI's (Command line interface) or 
	- Batch interface (Interactions happen with script files)

-  Program Execution
	The operating system allow for processes to execute using the CPU, a process must be able to either normally or abnormally.

-  **I/O operation**
	The OS provides the framework to acces and control I/O devices  

- **File System Manipulation**
	The operating system manages the file system in a computer and it allow other programs to act and access the file system.

- **Communication** 
	IPC (inter process communication), Process communications to processes on other devices over the network.

- **Error Detection**
	Provide logs and debug information as well as fall back services and process restart protocols to ensure the computer does not crash immediately.

- **Resource Allocation**
	Allocate file storage as well as CPU cycles and other allocations of resources to processes.

- **Accounting**
	` journalctl ` basically basically 

- **Protection**
	Process isolation, passwords 

## System Bootstrap process
The bootstrap program locates the OS kernel and loads into memory, the program is  usually stored in the read only memory of the computer
the init process ithe the first system process in Unix based systems.
The system awaits triggers which are either hardware or software (system calls or called monitor call). 

## System Calls
System calls are the Interfaces the operating system provides for process to make use of the functionalities the operating system provides.

### Program executions
#important
Two types of program execution: (switching between the modes is called context switching

#### User Mode 
The process executes as the user and it does not have direct acces to memory h/w & resources, this is the default runtime, program crashes should not really affect the whole operating systems. usually safer to execute.

#### Kernel Mode
The process executes ad the kernel which means it has all the permissions to acces memory hardware resources (better than sudo), The process crashes here the entire system may crash

A process can switch modes by calling the [[#System Calls]]

```
Kernel is the core of the system which is also the first program that launches when the computer boots
```

### Types of System Calls
#table

| Category                |                                                                                                                               |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Process Control         | end, abort, load , execute, create process, terminate process, get proc attributes, wait for time, wait events, signal event  |
| File Manipulation       | create file, delete file, open, close, read, write, reposition, get/set file attributes                                       |
| Device Manipulation     | request/release device, read , write, reposition, get/ device attributes , logically attach or detach devices                 |
| Information Maintenance | get/set time or date, get/set system data, get/set process or file or device attributes                                       |
| Communication           | Create/delete communication connections , send/receive messages, transfer states information, attach or detach remote devices |

## [[Topics/Operating System Structure|Operating System Structure]]
#important 
There are many was we can structure an operating system
-  Simple structure
-  Monolithic
-  Layered
-  Microkernel
-  Modular