 ![[Topics/Producer Consumer|Producer Consumer]]

```c
item next_produced;

while (true) {
	while (((in + 1) % BUFFER_SIZE)== out)
		;
	buffer[in] = next_produced;
	in = (in +1) % BUFFER_SIZE;
	
}
```

```c
item next_consumed;

while (true) {
	while (in == out)
		;
	next_consumed = buffer[out]
	out = (out +1) % BUFFER_SIZE;
	
}
```

## Race Condition and Critical Section

### Race Condition
The race condition is a situation when several process try to acces or modify the same piece of data simultaneously, the final output of the data is dependent on the order of the events happening.

### Critical Section
The critical section is the part of the program that contains the part of code that can cause a race condition, to avoid the race condition for concurrently executing process we can only execute one critical section at a time.

## The Critical Section Problem
This problem focuses on the fact that we have to design a which implements the following traits:
1. **Mutual exclusion** : No two critical sections are to be executed together 
2. **Progress** : When processes want to join, processes which have not yet entered the CPU only have the chance to do so
3. **Bounded waiting** : For each process there is a limit on the number of times it can enter the CPU.

### Peterson's Solution (Software Solution)
#important 
Its an algorithmic approach of solving the critical section problem, its restricted to only two process, the processes alternate between the critical section and the remainder sections. The solution makes use of two data items
```c
int turn
bool flag[2]
```
The turn variable is used to indicate which process gets to go the critical section, meanwhile the flag is used to indicate if the process is ready to enter the critical sections

```c
do{
	flag[i] = true;
	turn = j;
	while (flag [j] && turn == [j]);
	//critical secion
	flag [i] = false;
	//remainder section
} while (TRUE)
```

```c
do{
	flag[i] = true;
	turn = i;
	while (flag [i] && turn == [i]);
	//critical secion
	flag [j] = false;
	//remainder section 
} while (TRUE)
```

-  Provable that the three CS requirement are met:
	- Mutual exclusion is preserved
	- Progress requirement is satisfied
	- Bounded-waiting requirement is met

## Synchronization Hardware

- ### Test and Set
	This is an atomic instruction, that if both of the test and set instructions are executed the mutual lock in the system means that only one atomic process can have the lock at a given time and only when the said process releases the lock can another process take over.

- ### Compare and Swap
	This instruction set makes use of 3 variable being **address, expected value, new value** in this process we check if the expected value is which is the condition for execution, is matching the current value which is derived from the address (which is usual a lock address), and we can start the process execution, then we can set the it back to the expected value.

#difference 

| Aspect             | Test and Set (TAS)                                               | Compare and Swap (CAS)                                                                          |
| ------------------ | ---------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Atomic Operations  | Combined Test and Set                                            | Separate Read, Compare, and Set operations                                                      |
| Retry and Spinning | Continuously retries atomic operation (Busy-waiting)             | Decides what to do next on comparison failure (e.g., retry or take alternative action)          |
| Use Cases          | Simpler implementation, but can lead to inefficient busy-waiting | Versatile, used in designing lock-free algorithms and data structures for efficient concurrency |

### Mutex Locks
The hardware-based solutions to the critical-section problem are complicated as well as generally inaccessible to application programmers. From the perspective of the program, a mutex lock is a Boolean variable which indicates the availability of a slot in the CPU for execution. If said lock is available then the process acquires the lock and starts execution and on finishing set it back to available.

#disadvantage

### Disadvantage of using Mutex Locks 
The main problem we may face is the busy waiting, a process may end up in the process of waiting for a long time, and ends up calling the acquire function a lot of times. This is also called the spinlock because the process keeps running in the background until it gets the chance to use the CPU.

## Semaphores 
Semaphores are software solutions which were initially proposed by Dutch Scientist Edger Dijkstra, they behave similar to mutex locks but proved more sophisticated ways to synchronize processes. 

Semaphores are integer variables typically part of the operating system or the programming language, It can only be accessed using two atomic operations:
- wait() : P, which comes from the Dutch word proberen, which means to test.
- Signal() : V, from the word verhogen, which means to increment in Dutch.

```c
wait(S){
	while (S<=0);
	S - -;
}

Critical Secion 

signal(S){
	S++;
}
```

The process checks for S which is the number of processes which the CPU can execute, the principle behind semaphore is that when it is possible to use the CPU  a process reduces 1 from the S and starts executing, the process cannot execute if S is < 1 or, and also note that after completing the process the S value is incremented by the process by 1, to let other process know that it has finished execution.

### Types of Semaphores
According to the range of S we can classify semaphores into two types:
- **Binary** - S has two values either 0 or 1
- **Counting** - S will have a bigger value, this mean it can accommodate multiple processes running at the same time.

Semaphore also suffer from the [[#Disadvantage of using Mutex Locks]] 

### Solution to Busy Waiting
When a process finds itself that it has to wait for the semaphore to become available, rather than trying to busy wait, what it can do is call the block method on itself and stop execution until it has been called by another process, When the semaphore becomes available the signal method can call the process and inform them that they can try to acquire the semaphore lock 

```c
typedef struct{
	int value;
	struct process *list;
} semaphore;

wait(semaphore *S){
	S->value--;
	if (S->value < 0){
			add this process to S->list;
			block();
		}
}

signal(semaphore *S) {
		S->value++;
		if (S->value <= 0) remove a process P from S->list;
		wakeup(P);
	}
}
```


## Deadlocks and Starvation
#important 
A deadlock situation occurs in concurrent systems when two or more processes (or threads) are unable to proceed because each is waiting for the other to release a resource that it needs to continue execution. As a result, the processes end up in a circular waiting state, and none of them can make progress. Deadlocks can lead to a system freeze, where no further work can be done, and the processes are effectively stuck.