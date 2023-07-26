## Memory Management
This is the task of subdividing the memory among different process is called memory management. We aim to find the most efficient way of utilizing the memory in the computer.

## Basic Hardware
Main memory and the registers built into the processor itself are the only general-purpose storage that the CPU can access directly. There are machine instructions that take memory addresses as arguments, but none that take disk addresses. Therefore, any instructions in execution, and any data being used by the instructions, must be in one of these direct-access storage devices. If the data are not in memory, they must be moved there before the CPU can operate on them. 

Registers are memory location that are built into the CPU and are accessible within 1 CPU cycle, to prevent taking more CPU cycles to fetch the memory in the main memory there will be cache in-between the main memory and CPU to temporarily hold data for faster access.

### Protection
For proper system operation we must protect the operating system from acces by the user processes. On multiuser systems we must separate memory of each user,  This protection must be provided by the hardware because the operating system doesn’t usually intervene between the CPU and its memory accesses. we can sperate per-process memory which isolates each process from each other and thereby providing privacy.

To separate memory spaces we determine legal range each process may acces and ensure that it can acces only that specified memory addresses, we store this using two registers
- Base register: stores the smallest legal physical memory address
- Limit register: the size of the legal range.

e.g. if the base register holds 300040 and the limit register is 120900, then the program can legally access all addresses from 300040 through 420939 (inclusive).

Any attempt by a program executing in user mode to access operating-system memory or other users’ memory results in a trap to the operating system, which treats the attempt as a fatal error. This prevents accidental data modification or retrieval and improves the security of the overall system


## Memory Management Techniques

![[Images/Pasted image 20230726151009.png]]

### Contiguous Memory Management
Each programs occupies a single contiguous block of storage locations, basically set of memory locations with consecutive memory addresses.

#### Single Contiguous Memory Management
Simplest memory management scheme used in the earliest generation of computer systems, there is a reserved memory allocation for the operating system and then the rest is used for the application programs, this single continuous memory is referred to as the single contiguous memory management.

#### Multiple Partitioning 
Rather than a single partition for the memory, this scheme divides the memory into multiple partitions. there are two ways you can do this

#### 1) Fixed/Static Partitioning
	The main memory is divided into several fixed sized partition.

We make use of different allocation policies namely
- First Fit
- Best Fir
- Worst Fit 
- Next Fit - Prefers the next available memory location irrespective of efficiency

#important 
##### Internal Fragmentation
The situation where the memory address allocated to a process is more than it required, one of the solutions to prevent internal fragmentation is to use variable/dynamic partitioning's 

#### 2) Variable/Dynamic Partitioning 
In this situation we make the partitions during runtime and allow the partitions to be varied in size making them fit exactly the size of the process and thereby removing the problem of internal fragmentation.

##### External Fragmentation
The memory situation may become non contiguous after a bit while doing variable/Dynamic partitioning, This will lead to us not having a single memory location big enough to run a big program, a solution to this is by compaction, i.e. whenever memory becomes free we pool it together, this technique is also called defragmentation.

### Non Contiguous Memory Management 
Non-contiguous memory management is a memory allocation technique used in computer systems to manage physical memory (RAM) in a way that allows processes to be allocated memory in non-contiguous or fragmented chunks. In contrast, contiguous memory management allocates memory in a contiguous, continuous block.
#important 
```
Logical Address is the memory of the process
```

Two possible methods for This type is
#### Segmentation
Segmentation is a memory management scheme in which a logical  address is made up of many segments, each segment is named and numbers and referred to by the number and it also has a length of the segment. 

A logical address consists of two parts: 
- A segment number, s
- offset to that segment, d
The segment number is used to identify the segment, the offset is value which is between 0 and the segment limit, when a segment is legal we add it to the segment base to produce the physical address in memory of a desired bit.
The segments map to the logical address.
##### Hardware
![[Images/Pasted image 20230726190845.png]]


#### Paging
By breaking physical memory into fixed sized block called frames, as well as breaking the process memory (logical memory) into block of the same size called pages. We basically slot the pages into available memory frames and map accordingly to provide the logical address the memory it needs.

The page and frame sizes are determined by hardware, usually its a power of 2 varying between 512 bytes to 1Gb per page.