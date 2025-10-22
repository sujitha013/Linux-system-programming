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
