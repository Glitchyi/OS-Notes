# Process management
## Processes and Programs
A program in execution is called a process, its a program which is loaded into the main memory and fed into the CPU 

Each process has multiple parts:
- **Text Section** - The code which is to be executed
- **Data Section** - The global and static variable defined at compile time or just before run time.
- **Stack** - The temporary data, such as function parameters, return addresses, local variables
- **Heap** - The dynamically allocated variables initiated during run time.

#difference

| Program                                         | Process                                                              |
| ----------------------------------------------- | -------------------------------------------------------------------- |
| Set of instructions designed to complete a task | Program in execution                                                 |
| Passive entity usually file or executable       | Active entity with program counter to point to next set of resources |
| Usually in the secondary memory                 | Held in the primary memory                                           |
| Requires only memory space                      | Requires CPU, Memory address, I/O during working                                                                     |

## Process state
A process has 5 states it can be in:
- New
- Ready
- Running
- Waiting
- Terminated

![[Images/Pasted image 20230722192255.png]]

### Program Control Block
It is a representation for a process, it is just a repository of the information of the process such as the *process state, process number, program counter, registers, memory limits, list of open files.. and more* 

## Process Scheduling 
The program that selects the process for the CPU to execute considering the process satisfies the condition for execution. 

### Scheduling Queues
The process are stored are queues in memory making sure that the CPU time is not wasted, there are three queues 
1) **Job Queue**
	The process that enter the system are added to this queue, process here are all the systems in the system weather they are ready or execute or not
2) **Ready Queue** 
	The process which are ready for execution are placed in this queue, the queue is usually stored as a linked list, because the next process should be executed immediately without wasting CPU cycles.
3) **Device Queue**
	 This queue contains the processes which are waiting for particular I/O devices. Each I/O device has its own queue.

## [[Topics/Schedulers|Schedulers]]


### Context Switching

## Inter Process Communication

### Producer Consumer Problem
#important 



[[Topics/Produces Consumer Problem|Produces Consumer Problem]]