There are different type of operating systems.

## Batch Operating System
### Details
No to be confused with batch files in windows, The users of batch do not interact directly with the computer directly. The Operating System determines which operations should be run to achieve maximum efficiency. Processing Jobs with similar need are run together as batches where process with similar requirements are run together. 
e.g.  Payroll Systems, Bank Systems.

### Problems
Lack of user interaction with the job means some programs may not work properly also user inputs  may be a trouble to execute. CPU goes idle because the speed of I/O devices is slower than the CPU. It is also hard to determine priority properly.

## Multiprogrammed System
### Details
- The operating system keeps a lot of jobs ready to execute in the memory and whenever it finds the CPU free it allocated the process in the memory and keeps the CPU busy, 
- The jobs are kept in a Job Pool, the OS is a bit memory intensive and executes the Jobs in the memory. 
- Whenever the process needs to  perform an I/O operation, the system pauses the program and works on another program while the initial program finishes the I/O operation.
- These OS's are fairly sophisticated and implement Job Scheduling and CPU scheduling to run at maximum effiency 
e.g. Windows, Unix

## Multiprocessor Systems
- Often refereed to as parallel systems or tightly coupled systems , they have more than one CPU and have them in sharing resources and have a solid communication between them.
- Due to the presence of multiple processors the work gets done faster.
- Increased reliability since multiple processors can act redundantly.

## Time Sharing  Systems
- Each process gets a certain amount of time which it executes and switches to another process rather than batch and multiprogram.
- The switch occurs frequently so that the user can still interact with the system.
- For multiple users each user is provided with a time slice, which that user is allowed to interact with the system.

## Realtime systems
Each process is completed in a predefined time, the time specification is rigid and if the CPU fails to complete it the system fails.
There are two flavors of realtime systems:
- Hard realtime systems
- Soft realtime systems

### Hard Real-Time Systems
- Hard real-time systems have strict and critical timing constraints that must be met without fail. In these systems, missing a deadline is considered catastrophic and may lead to system failure or severe consequences. Failure to meet the timing requirement may lead to a loss of control, data corruption, or endangering human lives. Examples of hard real-time systems include flight control systems, medical devices, automotive safety systems, and industrial control systems.

### Soft Real-Time Systems:
- Soft real-time systems also have timing requirements, but they are more lenient compared to hard real-time systems. In soft real-time systems, missing a deadline is undesirable but not catastrophic. The system can still function correctly, but the quality of service or user experience may degrade if timing constraints are not met. Examples of soft real-time systems include multimedia streaming, video conferencing, and online gaming.

## Distributed Systems
Make use of multiple processor to server multiple users, they communicate with various communication lines. these systems are also called loosely coupled systems.
#Advantages
Resource sharing, high speed data exchange. redundant processing load distributed on CPUs
