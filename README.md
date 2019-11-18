# Concurrency Programming


# Concurrency
Concurrency means executing multiple tasks at the same time but not necessarily simultaneously. 

It can be achieved in two way:

Context-Switching or Parallelism

# Context-Switching

If your computer has only one core, your CPU will go back and forth between multiple processes or threads. Example: Your Operating System is working on a process when suddenly received a system call from higher processes or threads. Your CPU will save the context of the currency process before it moves to the higher priority process or thread. When your CPU is done with the other process, it will restore the context of the saved previous process.



# Parallelism 

It means performing multiple tasks simultaneously. In the previous example, if you had multiple-core, your CPU would be able to perform both processes simultaneously.

In a multi-core environment, concurrency can be achieved via parallelism in which multiple tasks are executed simultaneously. 




# Threads

There can be a situation where we would like to stop the threads such as to clean up the resources kept by thread or in case of misbehaving.

There can be multiple ways to stop the thread.

1) Thread.interrupt()

The interrupt is available to each thread object to interrupt the ongoing thread. 

2) Thread.currentThread().isInterrupted() 

There can be a situation where the thread.interrupt() method is not stopping the working thread. To force a thread to stop, we can write if statement to check whether we have a signal to interrupt the thread.

```
if (thread.currentThread().isInterrupted())
      System.out.println("Thread is interruped");
```  


3) Daemon Threads

Daemon threads low priority thread where it can't prevent JVM from stopping the execution. We would like to change to the priority of our thread (make it daemon thread) so that won't continue execution when we interrupt the thread, i.e., ```thread.interrupt()``` .

```
thread.setDaemon(true);
        
thread.start();

thread.interrupt();
```

With this method, we don't need ```if (thread.currentThread().isInterrupted())``` to stop the execution of the thread.

This is a way to prevent a thread from blocking our app from exiting. 

## Critical Section

The critical section is a code segment that includes shared resources. The operation on it needs to be Atomic, in other words, only one thread should have access to the critical section while others are waiting for permission.

To synchronize thread access on shared resources, java provides synchronized blocks with two different tastes, object-level or method level.

Have a look at code!

But, what operations in Java are atomic and don't need to get synchronized?

All reference assignments are atomic (including the getters and setters)
All primitive data types except double and long. Java doesn't guarantee atomicity on these operations. To synchronize them, **volatile** keywoard is used. 

## Notes

Reference variables are allocated in the heap if they are a class member, if not, they will be allocated in the stack and will point to object which is in Heap.

Threads cannot share local variables which are stored in the stack section of the memory. The reason: Local variables and parameters allocate on a thread's method-call stack. As a result, each thread receives its copy of those variables. In contrast, threads can share class fields and instance fields because those variables do not allocate on a thread's method-call stack. Instead, they allocate in shared heap memory—as part of classes (class fields) or objects (instance fields).
