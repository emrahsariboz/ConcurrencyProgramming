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

There can be situation where we would like to stop the threads such as to clean up the resouces kept by thread or in case of misbehaving.

There can be multiple way to stop the thread.

1) Thread.interrupt()

Interrupt is a awailable to each thread object to interrupt the ongoing thread. 

2) Thread.currentThread().isInterrupted() 

There can be situation where thread.interrupt() method is not stopping the working thread. In order to force thread to stop, we can write if statement to check whether we have a signal to intterupt the thread.

```
if (thread.currentThread().isInterrupted())
      System.out.println("Thread is interruped");
```  


3) Daemon Threads

Daemon threads low prioirty thread where it can't prevent JVM from stopping execution. We would like to chance to priority of our thread (make it daemon thread) so that won't continue execution when we interrupt the therad, i.e. , ```thread.interrupt()``` .

```
thread.setDaemon(true);
        
thread.start();

thread.interrupt();
```

With this method, we don't need ```if (thread.currentThread().isInterrupted())``` to stop the execution of the thread.
