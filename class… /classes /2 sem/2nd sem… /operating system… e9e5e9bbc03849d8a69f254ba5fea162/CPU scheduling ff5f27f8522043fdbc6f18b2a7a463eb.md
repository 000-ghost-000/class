# CPU scheduling

### CPU scheduling :

types :

- non-preemptive:
    
    Non-preemptive CPU scheduling allows a process to use the CPU until
    it finishes its task, even if there are higher-priority processes. This
    makes it predictable and simple, but it can lead to poor performance.
    Common algorithms include First-Come, First-Served, Shortest Job Next,
    and Priority Scheduling.
    
    - FCFS: The process that arrives first gets the CPU first.
    - SJN: The process with the smallest execution time is selected for
    execution next.
    - Priority Scheduling: A priority is associated with each process, and
    the CPU is allocated to the process with the highest priority.
- preemptive:
    
    Preemptive CPU scheduling allows the OS to reprioritize CPU control
    based on requirements. Useful in multitasking environments, it switches
    the CPU to new processes with shorter burst times than the current
    process, a process known as context switching. However, it may cause
    ‘starvation’ where a high burst time process is continually bypassed.
    Common algorithms include round-robin, Priority Scheduling, and Shortest
    Remaining Time First (SRTF).
    
    - i/o
    - time out
    - higher priority

### types of scheduling :

- Long-term: new to ready
- short term: ready to running
- midterm: swap out and swap in

### Scheduling criteria:

- CPU utilization
- throughput
- waiting time (WT)
- turnaround time (TA)
- response time