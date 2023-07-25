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

### The Critical Section Problem
This problem focuses on the fact that we have to design a which implements the following traits:
1. **Mutual exclusion** : No two critical sections are to be executed together 
2. **Progress** : When processes want to join, 
3. Bounded waiting

