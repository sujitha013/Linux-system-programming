## 1. What is meant by an IPC Mechanism?  
- IPC (Inter-Process Communication) mechanism is a method that allows multiple processes to communicate and share data with each other.It enables coordination and data exchange between processes running on the same or different systems.
## 2. Why we use IPC Mechanism?
-We use the Inter-Process Communication (IPC) mechanism when we need to exchange data or communicate between multiple processes. It allows processes to coordinate their actions and share information efficiently.
## 3.What are the types of IPC Mechanism's?
There are five main types of Inter-Process Communication (IPC) mechanisms:
- 1.Pipes
- 2.Named Pipes (FIFOs)
- 3.Shared Memory
- 4.Message Queues
- 5.Semaphores
## 4. What is meant by “unicast” and “multicast” IPC?
  - In IPC, unicast communication refers to data exchange between two related processes, such as a parent and child process created using the fork() system call.
  - Multicast communication, on the other hand, involves data exchange between multiple unrelated processes, allowing one process to send messages to several receiving processes simultaneously.
## 5. What is meant by PIPES?  
 - Pipes are an IPC mechanism that allow communication between two related processes, typically a parent and child process created using the fork() system call.
 -  Before creating a pipe, we need to define an integer array of two file descriptors:
 -  One for writing
 -  One for reading 
 -  These descriptors are automatically assigned to the next available indices in the file descriptor table.
 -  To create a pipe, we use the pipe() system call, which takes the array of file descriptors as an argument and sets up the communication channel between the      parent and child processes.
## 6. What is meant by Blocking Calls? 
- Blocking calls are system or function calls that pause the execution of a process or program until a specific event occurs, such as waiting for user input or data from another process. The process cannot proceed until the required action is completed.
## 7. What are the types of Blocking Calls?
  - There are different types of blocking calls in IPC, depending on the mechanism:
  - For pipes, the open() system call acts as a blocking call, pausing the process until the pipe is ready.
  - For named pipes (FIFOs), both open() and read() system calls can act as blocking calls, causing the process to wait until data becomes available.
## 8. What are the different types of I/O Calls?
  -Basic I/O calls, also known as universal I/O calls, include:
  - 1. open() – Opens a file or device.
  - 2.close() – Closes a file or device.
  - 3.read() – Reads data from a file or device.
  - 4.write() – Writes data to a file or device.
  - 5.ioctl() – Performs device-specific input/output operations.
  - 6.fcntl() – Performs various control operations on file descriptors.
- These calls form the foundation for performing input/output operations and controlling device behavior in most operating systems.
## 9. What are the I/O calls we are used in IPC Mechanisms?
- The frequently used I/O calls in IPC mechanisms are:
 - open() – Opens a communication channel (like a pipe or FIFO).
 - close() – Closes the communication channel.
 - read() – Reads data from the channel.
 - write() – Writes data to the channel.
## 10. What are the Blocking Calls used in IPC?
 - In IPC mechanisms, the major blocking calls are:
 - open() – Pauses the process until the communication channel (like a pipe or FIFO) is ready.
 - read() – Pauses the process until data becomes available on the channel.
 - These calls stop the execution of a process until the required data or message is available for communication.
## 11. What is meant by Named Pipes?
 - Named pipes (also called FIFOs) are an IPC mechanism used for communication between two unrelated processes.
 - A named pipe is created using the mkfifo() system call, which takes two arguments:
  - 1.The name of the file object
  - 2.Permissions for the pipe
-In typical usage, there is a server process that waits for requests and sends responses, and a client process that sends requests and waits for the responses.
-Named pipes are bidirectional, but for successful communication, the server and client must open the pipe in opposite modes (one for reading, the other for writing).
## 12. Where is the FIFO Object created?  
- A FIFO (named pipe) object is created as a special file in the filesystem using the mkfifo() system call.
- You provide a path or filename, and the operating system creates the FIFO at that location in the filesystem.
- The file acts as a communication channel between unrelated processes.
- ## Example:
- mkfifo("/tmp/myfifo", 0666);
- This creates a FIFO named myfifo in the /tmp directory with read/write permissions.
## 13. What is the call used to create a FIFO Object? 
 - To create a FIFO (named pipe) object, we use the mkfifo() system call.
 - It accepts two arguments:
 - Name of the FIFO file object
 - Permissions of the pipe
 - ## Example:
 - mkfifo("fifoobj", 0666);
 - This creates a named pipe called fifoobj with read/write permissions for all users.
##  14. What are the Blocking Calls used in Named Pipes? 
  - In named pipes (FIFOs), the blocking calls are:
  - open() – Pauses the process until the FIFO is opened by the other process.
  - read() – Pauses the process until data becomes available to read from the FIFO.
  - These calls ensure proper synchronization between the communicating processes.
## 15. Why read system calls acts as a blocking call?
  - The read() system call acts as a blocking call because when a server process opens a FIFO in read mode, it must wait for data from the client process.
    - The read() call pauses the execution of the server process until data is available to be read from the client.
    -  This ensures proper synchronization between the client and server.
## 16. Difference between the Named Pipes and Pipes? 
- ## Similarities:
   - Both pipes and named pipes (FIFOs) allow bidirectional communication
- ## Differences:
  - ## Pipe:
- Used only between related processes (e.g., parent-child)
- If there is no data, the process may terminate
- Created in memory using pipe() system call
- ## Named Pipe (FIFO):
- Can be used between unrelated processes
- If there is no data, the process blocks until data is available
- Created as a special file in the filesystem using mkfifo()
## 17. What is return value of read system call?  
- The read() system call returns:
  - -1 on failure and sets errno to indicate the error.
  - On success, it returns the number of bytes actually read from the file or communication channel.
  - If the end of file (EOF) is reached, it returns 0.
## 18. What is meant by message queue? 
- A message queue is an IPC mechanism used for communication between multiple unrelated processes.
   - It allows processes to send and receive messages in a queue, ensuring asynchronous and ordered communication.
   - Message queues overcome the limitations of pipes and named pipes, such as the lack of message prioritization and flexibility.
## 19. Why we use message queues? 
- We use message queues because they allow safe and efficient communication between multiple unrelated processes.
  - ## Key reasons:
   - Asynchronous communication: Sender and receiver don’t need to be active at the same time.
   - Ordered delivery: Messages are delivered in FIFO order (or by priority).
   - Avoids blocking: Processes don’t have to wait like in pipes or named pipes.
   - Message boundaries: Each message is treated as a separate unit, unlike streams in pipes.
 - ## Example use case:
  - A client sends multiple requests to a server, and the server can process them in order without losing messages.
## 20. What is difference between Named Pipe and Message Queue?  
 - ## Differences between Named Pipe and Message Queue:
  - ## Named Pipe (FIFO):
     - Bidirectional (data can flow both ways)
     - Used for communication between unrelated processes
     - Data is read in stream mode, without message boundaries
  - ## Message Queue:
   - Not bidirectional (messages have a specific sender and receiver)
   - Allows asynchronous communication between processes
   - Maintains message boundaries and priority, providing more control over data flow.
##21. What is the system call used to create the message queue?
- To create a message queue, we use the msgget() system call, which is defined in the <sys/msg.h> header file.
- The msgget() call accepts three arguments:
  - 1.Key – A unique identifier defined by the user.
  - 2.Permissions – Specifies access rights for the queue.
  - 3.Flag (e.g., IPC_CREAT) – Used to create the queue if it doesn’t already exist.
  -  ## Example:
  -  msgget(key, 0666 | IPC_CREAT);.
##22. Where was the message queue created?
-A message queue is created and maintained in the kernel space.
   -This allows it to be accessed by multiple processes for communication.
   - The kernel manages the storage, synchronization, and message ordering internally.
##23. What is meant by Shared Memory?
-Shared Memory is one of the Inter-Process Communication (IPC) mechanisms and is considered the fastest method among all IPC mechanisms.
      It allows multiple processes to communicate by sharing a common block of memory.
      The shared memory segment is created in the user space, and processes can access it using pointers to the base address.
      However, the major drawback of shared memory is the lack of synchronization — multiple processes can modify the same memory at the same time, which can         lead to data inconsistency.
 ##24. Why we use Shared Memory?
-We use Shared Memory when we want to avoid the overhead of system calls used for frequent process switching.
     It allows multiple processes to access the same memory segment directly, making communication faster and more efficient.
     Shared memory is ideal for situations where large amounts of data need to be exchanged quickly between processes.
##25. Difference between Shared Memory and Message Queues?
- ## Difference between Message Queue and Shared Memory.
   -  ## Message Queue:
       - Provides synchronization automatically
       - Slower because data is copied between kernel and user space
       - Requires system calls (msgget(), msgsnd(), msgrcv())
       - Stores messages in a queue structure in kernel space
       - Useful for discrete message exchange between processes       
   - ## Shared Memory:
      - Does not provide synchronization (requires semaphores/mutexes)
      - Very fast, as processes directly access the same memory segment
      - System calls needed only for creation and attachment (shmget(), shmat())
      - Stores data in a common memory block accessible by processes
      - Useful for sharing large amounts of data efficiently
  ## 26. What is use of stat command?
                  
     
     

 
