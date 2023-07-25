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

## Schedulers
The operating system chooses the process in the queues and prepares it for execution by the CPU.
```
I/O-bound process is one that spends more of its time doing I/O than it
spends doing computations.

A CPU-bound process generates I/O requests infrequently, using more of its
time doing computations.
```

### Long Term Schedulers
Also known as long term schedulers they load process from the job queue directly to memory of the system, the long term schedulers executes much less frequently, and it controls the number of process in the memory (Degree of multiprogramming). It selects a **good mix of I/O bound as well as CPU bound processes**. 

### Short Term Schedulers
Selects the processes which are ready to execute from the ready queue and then allocates them CPU cycles, the short term scheduler is responsible to feed the CPU with process without it wasting cycles, the scheduler executes atleast once every 100 milliseconds. It has less control of the degree of multiprogramming
#difference 

| Long Term                                        | Short Term                                              |
| ------------------------------------------------ | ------------------------------------------------------- |
| Chooses a process to be added to the ready queue | Chooses the process to be executed from the ready queue |
| Job Scheduler                                    | CPU Scheduler                                           |
| Slowe                                            | Faster                                                  |
| Chooses from the Job Pool                        | Chooses from the Ready Queue                            |

![[Images/Pasted image 20230722233939.png]]

### Medium Term Schedulers
Sometimes it is more efficient to remove the current process and reintroduce it later, this is called **swapping** and this is done by the medium term scheduler. Swapping is used to improve process mix which distributes the workload on the CPU.

![[Images/Pasted image 20230722234825.png]]


Operating system programs that are responsible for scheduling programs re called schedulers, there are mainly three types 
1) Long Term 
2) Short Term
3) Medium Term

### Context Switching
The process of switching process requires the saving and restoring of the state of the current process as well as the restoring the state of that process given, the saving process means the kernel saves the PCB of the process, and restoring the context is bringing it back to the CPU.

## [[Topics/Inter Process Communication|Inter Process Communication]]
Processes executing concurrently in the operating system maybe either independent or cooperating.

- **Independent Process**
	These types of process cannot affect or be affected by other process in the executing system, they also do not share with any other process.
- **Cooperating Process**
	There are two or more processes which affect each other or get affected by processes running in the system, 

### Shared Memory

#important 
### Message Passing
1) Naming
2) Synchronization 
3) Buffering

## Process Creation And Termination

### Creation 
A process can create many new processes, the process that creates said processed are called parent processes and the new process are children of that process. each of these process in turn may create more processes forming a tree of process, usually we use pid to identify the processes

For the execution of the child process there are two possibilities, 
1) The parent continues to execute concurrently with the child process 
2) The Parent wait until some or all of its children have finished execution and have been terminated.
Also the program could have been duplicated as the child or a new program might have spun up.

#### How UNIX systems create new process
```c
fork()          // System call to create a new proces 
exec()        // used to replace an existing 
wait()         // issued by a parent process , moves the process to the ready queue
```

### Termination
- **Normal Termination** - it finished executing its final statement, and asks the operating systems to delete it. 
```
exit() in UNIX and ExitProcess()
```
- **Cascading Termination** - The phenomena of termination of the child when the parent has terminated, if the parent is terminated normally or abnormally all the children must also be terminated.

#### Zombie process
When the parent starts a child process and on its end the parent doesn't pickup the exit code of the child, the process consumes no resources. This is a zombie process.

#### Orphan process
If a parent did not invoke wait and gets terminated instead the child process remains as orphans. UNIX and Linux handles orphans by assigning a new process to the orphans.

## CPU Scheduling
CPU scheduling deals with the problem of deciding which of the process in the ready queue is to be allocated to the CPU, the objective in the case of multiprogrammed systems is to maximize CPU utilization. 

The CPU scheduling decision take place when the process is switching between the states or termination of an event
1) Running to waiting
2) Running to ready
3) Waiting to ready
4) Termination 
1-4 is non preemptive, all other scheduling is preemptive
> ref [[#Process state]]

### Dispatcher
The dispatcher is the module that gives control of the CPU to the process selected by the [[#Short Term Schedulers]], the function of the dispatcher includes switching context, switching to user mode, restarting the programs
> Dispatcher Latency is the time taken to stop one process and start another

### Scheduling Criteria
Scheduling algorithms have different criteria to select the  processes some of the criteria that algorithms use are:
- **CPU utilization**  - Objective is keep the CPU as busy as possible
- **Throughput** - Focuses more on the number of processes completed in a unit time
- **Turnaround time** - Focuses on the time interval of submission to the time of completion
- **Waiting time** - Sum of the periods spent waiting in the ready queue
- **Response time** - Time taken to get the first response

### [[Topics/Scheduling Algorithms |CPU Algorithms ]]
1. First-Come, First-Served Scheduling
2. Shortest-Job-First Scheduling
3. Priority Scheduling
4. Round-Robin Scheduling
5. Multilevel Queue Scheduling
6. Multilevel Feedback Queue Scheduling
#important 
