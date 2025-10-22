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
 -  To create a pipe, we use the pipe() system call, which takes the array of file descriptors as an argument and sets up the communication channel between the parent and child processes.
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
- ## 9. What are the I/O calls we are used in IPC Mechanisms?
- The frequently used I/O calls in IPC mechanisms are:
 - open() – Opens a communication channel (like a pipe or FIFO).
 - close() – Closes the communication channel.
 - read() – Reads data from the channel.
 - write() – Writes data to the channel.
 - ## 10. What are the Blocking Calls used in IPC?
 - In IPC mechanisms, the major blocking calls are:
 - open() – Pauses the process until the communication channel (like a pipe or FIFO) is ready.
 - read() – Pauses the process until data becomes available on the channel.
 - These calls stop the execution of a process until the required data or message is available for communication.
 - ## 11. What is meant by Named Pipes?
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
