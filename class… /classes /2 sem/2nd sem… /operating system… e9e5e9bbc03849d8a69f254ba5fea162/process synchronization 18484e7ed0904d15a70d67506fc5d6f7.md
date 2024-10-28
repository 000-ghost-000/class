# process synchronization

### process synchronization :

concurrent access to shared data may result in data inconsistency

when one process executes in a critical section no other process is to be allowed to execute in its critical section the execution of critical section is mutually exclusive in time

Semaphore is a synchronization tool to deal with critical section problem integral value 

wait(s) {s=1}

`while s≤0 do no operation`

`s=s-1;`

signal (s) 

`s=s+1;`

`repeat`

wait(s)

`critical section`

signal(s)

`remainder section;`

`until false;`

the problem with this is busy waiting  that the s is waiting continuously so to solve this issue we redefine wait and signal

Process synchronization is a critical concept in operating systems that ensures multiple processes running concurrently can access shared resources and data without causing conflicts or inconsistencies. Here are some key points to remember:

**Why is Synchronization Important?**

Imagine multiple programs running on your computer:

- A web browser needs to update a shopping cart stored in memory.
- A music player needs to access the sound card for audio playback.
- An email client might be downloading attachments concurrently.

Without synchronization, these processes could access the same resources (memory, files, devices) at the same time, potentially leading to:

- **Data corruption:** If two processes try to modify the same data simultaneously, the resulting data might be inconsistent.
- **Incorrect results:** Incomplete or inaccurate computations can occur if processes rely on shared data that is being updated by another process.

**Synchronization Mechanisms:**

Operating systems provide various tools for process synchronization to ensure orderly access to shared resources. Here are some common methods:

- **Mutual Exclusion:** Guarantees that only one process can access a critical section of code (where shared resources are modified) at a time. Common mechanisms include:
    - **Mutexes:** Locks that a process acquires before entering a critical section. Other processes are blocked until the lock is released.
    - **Semaphores:** Generalization of mutexes, allowing control over access to a limited number of resources (not just one).
- **Monitors:** High-level constructs that encapsulate both data and the procedures that operate on that data. Only one process can be inside a monitor at a time, ensuring proper synchronization.
- **Critical Sections:** Explicitly designated code segments where shared resources are accessed. Synchronization mechanisms are used to ensure only one process executes within a critical section at a time.

**Synchronization Considerations:**

- **Deadlocks:** A situation where two or more processes are waiting for resources held by each other, creating a permanent stall. Careful design and resource management are crucial to avoid deadlocks.
- **Starvation:** A process might be continuously denied access to shared resources due to higher-priority processes constantly acquiring them. Scheduling algorithms and fair resource allocation strategies can help prevent starvation.

**Choosing the Right Synchronization Mechanism:**

The choice depends on the specific needs of the application and the level of granularity required for resource access control. Mutexes offer a simple solution for single resource access, while semaphores provide more flexibility for managing multiple resources. Monitors can be suitable for high-level data protection with encapsulated procedures.

wait(s)

 `s.value=s.value-1;`

`is s.value<0`

`then begin`

`add tis process to s.l(l is a list associated with sempaphore s)`

`block;`

`end`

signal(s)

`s.value=s.value+1;`

`if s.value≤0`

`then begin`

`remove a process p from s.l;`

`wakeup(p)`

`end`

### classical synchronization on problem:

- readers writers problem
    
    [reader writer java code](process%20synchronization%2018484e7ed0904d15a70d67506fc5d6f7/reader%20writer%20java%20code%206793dfacd7e7445c88f760a94615ea66.md)
    
- dining philosopher problem
- bounded buffer problem