#important 
The producer consumer problem is a multi-program synchronization program, wherein two processes one producer and another consumer are working concurrently the require both of them to work together in order to properly function. A real world example would be of a website where the web server sends the HTML to the client process on request.

One solution to the producer consumer problem is shared memory, we create a buffer for the producer to keep producing resources that the consumer requires to execute properly, the synchronization part comes in ensuring that the consumer doesn't start using resources which are not yet produced by the consumer.

There can be two types of buffers: 
- **Unbounded** - it is a buffer without any size limitations.  
- **Bounded** - Contrary this would be a fixed size buffer

```
The consumer will have to wait if the buffer is empty

The consumer should wait if the buffer is full
```
