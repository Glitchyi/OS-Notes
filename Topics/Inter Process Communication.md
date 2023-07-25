## Reasons for process co-operation 
In a multiprogrammed system it is important to allow processes to communicate for several reason:
1) **Information Sharing** - Several process/users in the same information must provide an opportunity for concurrent access
2) **Computation Speedup** - Breaking down tasks into subtasks makes them faster.
3) **Modularity** - Breaking down of the system into a modular fashion, dividing the system into sperate processes or threads.
4) **Convenience** - Isolation and separation of task based on the user help us manage preferences for each user more easily.

## Models of Inter-process Communication
There are two fundamental models of interprocess communication:
- **[[#Shared Memory]]** - A region of shared memory is accessed by the process involved in communication and information to be shared is placed in this common region.
- **[[#Message Passing]]** - Process send and receive information by the means of sending and receiving messages. This technique is better for small amounts of data.

### Shared Memory 
For shared memory interprocess communication the system allocates a shared memory space for each of the process involved and allows them to write and read information from the space provided, this means the process can write the information they want to send to the other process in the shared memory address and the receiver process can just read it from the shared memory. All the involved process will attach themself to the shared memory, and are held responsible for not writing and reading at the same location.
[[Topics/Producer Consumer|Producer Consumer|]]


### Message Passing
The method of passing of messages to provide communication between processes, It allows the process to communicate without the allocation of shared space, this paradigms of IPC is better in the case of distributed systems too.

For processes to communicate between them they gave have to have a communication link which can be implemented in multiple ways:
- **[[#Naming]]** - Direct or indirect communications
- **[[#Synchronization]]** - Synchronous or asynchronous 
- **[[#Buffering]]** - Automatic of explicit buffering

#### Naming
Process which want to communicatee can do so using two methods either direct or indirect
- **Direct Communication** 
	Each process must explicitly name the recipient or sender for the communication link to be formed.
	The send and receive primitives are defined as: 
```
Send(<Process Name 1>, message)          Sending information to process 1
Recive(<Process Name 2>, message)      Reciving informaiton from process 2
```
- **Indirect communication** 
	The messages are set and received from mailboxes or ports respectively, **Mailbox** is an object into which messages can be placed by process and from which messages can be removed each mailbox has unique identification, this makes it easier for process to communicate between each other by having a unique shared mailbox.
``` 
Send(<Mailbox address A>, message)               Send a message to mailbox A
Receive(<Mailbox address A>, message)          Receive a message from mailbox A
```

#### Synchronization 
Synchronous communication between process takes place through calls to send and receive primitives, message passing in the scheme maybe blocking (synchronous) or non-blocking(asynchronous)
- **Blocking send** - The sending process is blocked until the message is received i.e. one message at a time.
- **Non Blocking send** - The process resumes normally after sending a message
- **Blocking receive** - The receiver blocks execution until a message is received
- **Non Blocking receive** - The receiver retrieves either a valid message or null

#### Buffering
Buffering is basically making temporary queues to store messages, such queues can be implemented in three ways:
- **Zero Capacity** - The queue has a maximum length of zero i.e. the sender blocks until the recipient receives.
- **Bounded Capacity** - The queue has a finite length, the sender blocks when the queue is full, the links capacity is finite.
- **Unbounded Capacity** - The messenger never blocks there is an infinite capacity for messages in the queue.