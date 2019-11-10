# Concurrency Programming


# Concurrency
Concurrency means executing multiple tasks at the same time but not necessarily simultaneously. 

It can be achieved in two way:

Context-Switching or Parallelism

# Context-Switching

If your computer has only one core, your CPU will go back and forth between multiple processes or threads. Example: Your Operating System is working on a process when suddenly received a system call from higher processes or threads. Your CPU will save the currency on the CPU before the move to the higher priority process or thread. When your CPU is done with the other process, it will restore the context of the saved previous process.



# Parallelism 

It means performing multiple tasks simultaneously. In the previous example, if you had multiple-core, your CPU would be able to perform both processes simultaneously.

In a multi-core environment, concurrency can be achieved via parallelism in which multiple tasks are executed simultaneously. 


