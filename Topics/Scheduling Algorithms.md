#important 
# Important Terminology 

|Term|Meaning|
|---|---|
|Process|Usually the process ID|
|Burst Time BT|It is the amount of time the process needs to finish execution|
|Arrival Time AT|The instance of time when the process arrives at the queue|
|Completion Time CT|The instant of time when the process finishes execution|
|Turn Around Time TAT|Total time to complete execution (Completion time - Arrival time)|
|Waiting Time WT|Total time the process waits in the ready queue (Turn around time - Burst time)|

# The Algorithms

1. [[#First-Come, First-Served Scheduling]]
2. [[#Shortest-Job-First Scheduling]]
3. [[#Priority Scheduling]]
4. [[#Round-Robin Scheduling]]
5. [[#Multilevel Queue Scheduling]]
6. [[#Multilevel Feedback Queue Scheduling]]

## Gantt Chart 
This is the illustrative representation of a schedule by  plotting the time of each process as a bar
e.g.![[Images/Pasted image 20230725193515.png]]

## First-Come, First-Served Scheduling
This it the simplest of the scheduling algorithms, its often shortened as FCFS, the algorithm follows the order which the processes arrive. There is a queue which keeps note of the order of the process, and as the name suggest the process allocates the first process which arrived to the CPU for execution.

## Shortest-Job-First Scheduling
In this type of scheduling the CPU gets allocated with the process with the least burst time, it dosent care about the order in which the process arrived it chooses the shortest process **currently in** the queue.

## Priority Scheduling
This scheduling algorithm gives importance to the priority of a process rather than arrival time or the burst time of that process.

## Round-Robin Scheduling
The Round Robin scheduling algorithm makes use to a concept of limiting each process to a specific amount of time, and if the process has not finished it removes the process and adds it back to the ready queue and make it go again until it gets over, this is followed for all the process in the queue.

## Multilevel Queue Scheduling
Multilevel Queue Scheduling is a CPU scheduling algorithm that partitions the ready queue into several separate queues, each with its priority level. Processes are then assigned to these queues based on their characteristics or priority. The objective is to give different priorities to different types of processes and serve them accordingly. It is one of the variations of the basic multilevel scheduling concept.

## Multilevel Feedback Queue Scheduling
Multilevel Feedback Queue Scheduling is an extension of the multilevel queue scheduling algorithm, designed to address the limitations of fixed-priority scheduling and provide better performance for dynamic workloads. It allows processes to move between different queues based on their behavior, ensuring that CPU scheduling adapts to changing workload characteristics.