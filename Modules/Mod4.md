## Memory Management
This is the task of subdividing the memory among different process is called memory management. We aim to find the most efficient way of utilizing the memory in the computer.

## Basic Hardware
Main memory and the registers built into the processor itself are the only general-purpose storage that the CPU can access directly. Machine Instructions take 

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

