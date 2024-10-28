# scheduling algorithm

### scheduling algorithm:

- first in first out (FIFO) / first come first serve (FCFS)

[first come first serve code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/first%20come%20first%20serve%20code%20654824c5ea264e65879774b7465fbe9c.md)

[first come first serve code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/first%20come%20first%20serve%20code%20654824c5ea264e65879774b7465fbe9c.md)

First-Come, First-Served (FCFS) is a non-preemptive scheduling
algorithm in operating systems. In this method, the process that arrives
first is the one that gets the CPU first. This approach is simple and
predictable, but it can lead to poor performance if a long process
arrives before shorter ones, causing the shorter ones to wait, a
situation known as the convoy effect.

(*TA*) = *complition* − *arrival*

*avg*(*TA*) = (*TA*1+*TA*2...*TAn*)/*n*

*WT* = *TA* − *burst*

*avg*(*WT*) = (*WT*1+*WT*2...*WTn*)/*n*

*response* = *got*(*CPU*) − *arrival*

- shortest job first (SJF)

[shortest job first code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/shortest%20job%20first%20code%20544c7d1dfbcd41f3b60e520e658b3693.md)

[shortest job first code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/shortest%20job%20first%20code%20544c7d1dfbcd41f3b60e520e658b3693.md)

Shortest Job First (SJF) is a CPU scheduling algorithm in which the
process with the smallest execution time is selected for execution next.
It can be either preemptive or non-preemptive:

- **Non-preemptive SJF** scheduling executes the current
process to completion before moving on to the next one. While simple and
predictable, it can lead to poor performance if a long process arrives
before shorter ones.
- **Preemptive SJF**, also known as Shortest Remaining
Time First (SRTF), allows the operating system to interrupt the
currently running process if a new process arrives with a shorter
remaining time. This can minimize waiting time and improve
responsiveness, but it may also lead to higher overhead due to frequent
context switching.

Key points:

- SJF is optimal in terms of average waiting time for a given set
of processes, but it is often impractical due to the difficulty of
accurately predicting the time a process will take.
- It can lead to starvation if shorter processes keep
arriving.
- It is appropriate for batch systems where jobs can be run to
completion, but less so for interactive systems where processes may not
have a predictable running time.
- priority scheduling
    
    Priority scheduling is an algorithm used in operating systems to
    manage processes based on their priority. In this system, each process
    is assigned a priority, and the CPU is allocated to the process with the
    highest priority.
    
    Key features of this system include:
    
    - **Preemptive and Non-preemptive:** Priority scheduling
    can be either preemptive, where higher-priority processes can interrupt
    lower-priority ones, or non-preemptive, where processes run to
    completion before switching, even if a higher-priority process
    arrives.
    - **Dynamic and Static Priority:** In dynamic priority
    scheduling, priorities can change based on system events or resource
    usage. In static priority scheduling, priorities remain fixed throughout
    execution.
    
    Advantages of priority scheduling are improved responsiveness for
    high-priority tasks, reduced waiting time for important processes, and
    efficient management of time-sensitive operations.
    
    However, the disadvantages include potential for starvation of
    low-priority processes, increased overhead due to context switching in
    preemptive versions, and challenges in determining appropriate priority
    assignment.
    
    Priority scheduling is commonly used in real-time systems where
    deadlines are critical, operating systems managing multiple applications
    with varying importance, and task scheduling in servers and
    multi-process systems.
    
- round robin (RR)
    
    Round Robin (RR) is a CPU scheduling algorithm in operating systems
    where each process in the ready queue takes turns to execute in fixed
    time slots or quantum.
    
    Key Features:
    
    - Fairness: Each process gets an equal chance to run, preventing any
    process from monopolizing the CPU.
    - Responsiveness: Frequent context switches lead to faster perceived
    response times.
    - Improved Multiprogramming: Ensures fair CPU allocation for managing
    multiple processes.
    
    Drawbacks:
    
    - Overhead: Frequent context switching can increase the overhead due
    to the cost of saving and restoring process states.
    - Unfair for Real-time Processes: Processes with strict timing
    requirements may not meet their deadlines due to fixed quanta.
    - Optimal Quantum Selection: The choice of quantum length is crucial
    in striking a balance between fairness and overhead.
    
    Round Robin is commonly used in web servers handling numerous short
    requests, operating systems managing background processes, and
    time-sharing systems allowing multiple users concurrent access.
    
- multilevel queue scheduling
    
    Multilevel Queue Scheduling in Operating Systems:
    
    - Multilevel Queue Scheduling is a complex CPU scheduling algorithm
    that segregates the processes into various scheduling queues based on
    their properties.
    - Each queue has its own scheduling algorithm. For instance, one queue
    can follow a First-Come-First-Served approach, another can implement
    Priority Scheduling, and so forth.
    - The queues are ordered in a hierarchy based on their priority. The
    CPU gives precedence to the processes in the highest priority queue. If
    the highest priority queue is empty, it moves to the next queue.
    - Multilevel Queue Scheduling is beneficial when processes can be
    clearly categorized based on their CPU requirements. For example, system
    processes, interactive processes, and batch processes can have their
    separate queues.
    - A significant limitation of this scheduling algorithm is its
    rigidity. Once a process is assigned to a queue, it cannot be moved to
    another queue.
    - To overcome this limitation, Multilevel Feedback Queue Scheduling
    can be used, which allows the processes to move between queues based on
    their behavior.
- shortest remaining time (Preemptive version of SJF):

In operating systems, **Shortest Remaining Time (SRT)**,
also known as **Shortest Job First (SJF)** preemptive, is a
scheduling algorithm that prioritizes processes with the least amount of
remaining execution time. This means the process closest to completion
gets the CPU next, regardless of when it arrived in the system.

![https://media.geeksforgeeks.org/wp-content/uploads/20210920190203/gfgupdated.jpg](https://media.geeksforgeeks.org/wp-content/uploads/20210920190203/gfgupdated.jpg)

https://media.geeksforgeeks.org/wp-content/uploads/20210920190203/gfgupdated.jpg

**Here’s how it works:**

1. All processes waiting for the CPU are ranked in a queue based on
their remaining execution time.
2. The process at the head of the queue with the shortest remaining
time gets assigned the CPU.
3. While the currently executing process runs, the remaining execution
time of other processes in the queue may decrease.
4. If a new process arrives with a shorter remaining time than the
currently running process, it will preempt (interrupt) the running
process and be placed at the head of the queue.
5. This cycle continues until all processes are completed.

**Advantages of SRT:**

- **Minimizes average waiting time:** Processes with
little remaining time finish quickly, reducing the overall wait for all
processes.
- **Improves turnaround time:** The average time it takes
for a process to be completed from submission to execution is faster
than other scheduling algorithms like First Come First Served
(FCFS).
- **Reduces starvation:** Even low-priority processes
with short remaining times eventually get their turn, unlike FCFS where
they might wait indefinitely.

**Disadvantages of SRT:**

- **Overhead:** Frequent context switching due to
preemption can negatively impact performance.
- **Difficult to implement:** Accurately predicting
remaining execution time for processes can be challenging.
- **Not suitable for systems with unknown execution
times:** If you don’t know how long a process will take to run,
SRT can’t prioritize it effectively.

## round robin:

[round robin code](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/round%20robin%20code%20ab2a4a30b58446f59cc7b333f8364ff8.md)

[round robin code](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/round%20robin%20code%20ab2a4a30b58446f59cc7b333f8364ff8.md)

**Concept:**

- A CPU scheduling algorithm where processes take turns running
for **fixed time quanta** before being preempted and placed
at the back of the queue.
- Ensures **fairness** and
prevents **starvation** for processes waiting for CPU
time.

**Key Benefits:**

- **Fairness:** Each process gets an equal chance to
run, unlike FCFS where long-running processes can monopolize the
CPU.
- **Reduced waiting time:** All processes progress
quickly, even those with short burst times.
- **Increased responsiveness:** Users experience faster
response times due to frequent context switches.
- **Improves multiprogramming performance:** Efficiently
manages multiple processes by ensuring fair CPU allocation.

**Drawbacks and Considerations:**

- **Overhead:** Frequent context switches can increase
overhead due to saving and restoring process states.
- **Unfairness for real-time processes:** Processes with
strict timing requirements may not meet deadlines with fixed
quanta.
- **Choosing the right quantum:** Selecting an optimal
quantum is crucial for balancing fairness and overhead.

**Parameters to Consider:**

- **Quantum (time slice):** Determines how long a process
can run before being preempted.
- **Scheduling overhead:** Cost of switching between
processes, affecting overall efficiency.
- **Arrival order:** Can be ignored (pure RR) or
considered (priority RR) for fairness and responsiveness.

**Examples of Use:**

- Web servers handling numerous short requests.
- Operating systems managing background processes.
- Time-sharing systems allowing multiple users concurrent access.

**Comparison with Other Algorithms:**

- **FCFS:** Less fair, may lead to starvation for short
processes.
- **Priority:** Can prioritize certain processes, but
fairness for lower-priority tasks can suffer.
- **Non-preemptive:** Processes run to completion before
others get CPU time, potentially leading to starvation.

# Examples
to show working of Round Robin Scheduling Algorithm

*Example-1:* Consider the following table of arrival time and
burst time for four processes *P1, P2, P3, and P4* and
given *Time Quantum = 2*

| Process | Burst Time | Arrival Time |
| --- | --- | --- |
| P1 | 5 ms | 0 ms |
| P2 | 4 ms | 1 ms |
| P3 | 2 ms | 2 ms |
| P4 | 1 ms | 4 ms |

The Round Robin CPU Scheduling Algorithm will work on the basis of
steps as mentioned below:

*At time = 0,*

- The execution begins with process P1, which has burst time 5.
- Here, every process executes for 2 milliseconds (*Time Quantum
Period*). P2 and P3 are still in the waiting queue.

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0-2ms | P1 | 0ms | P2, P3 | P1 | 2ms | 5ms | 3ms |

*At time = 2,*

- The processes P1 and P3 arrives in the ready queue and P2 starts
executing for *TQ* period

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2-4ms | P1 | 0ms | P3, P1 | P2 | 0ms | 3ms | 3ms |
|  | P2 | 1ms |  |  | 2ms | 4ms | 2ms |

*At time = 4,*

- The process P4 arrives in the *ready queue*,
- Then P3 executes for *TQ* period.

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 4-6ms | P1 | 0ms | P1, P4, P2 | P3 | 0ms | 3ms | 3ms |
|  | P2 | 1ms |  |  | 0ms | 2ms | 2ms |
|  | P3 | 2ms |  |  | 2ms | 2ms | 0ms |

*At time = 6,*

- Process P3 completes its execution
- Process P1 starts executing for *TQ* period as it is next in
the b.

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 6-8ms | P1 | 0ms | P4, P2 | P1 | 2ms | 3ms | 1ms |
|  | P2 | 1ms |  |  | 0ms | 2ms | 2ms |

*At time = 8,*

- Process P4 starts executing, it will not execute for *Time
Quantum period* as it has burst time = 1
- Hence, it will execute for only 1ms.

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 8-9ms | P1 | 0ms | P2, P1 | P4 | 0ms | 3ms | 1ms |
|  | P2 | 1ms |  |  | 0ms | 2ms | 2ms |
|  | P4 | 4ms |  |  | 1ms | 1ms | 0ms |

*At time = 9,*

- Process P4 completes its execution
- Process P2 starts executing for *TQ* period as it is next in
the *ready queue*

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 9-11ms | P1 | 0ms | P1 | P2 | 0ms | 3ms | 1ms |
|  | P2 | 1ms |  |  | 2ms | 2ms | 0ms |

*At time = 11,*

- Process P2 completes its execution.
- Process P1 starts executing, it will execute for 1ms only

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 11-12ms | P1 | 0ms |  | P1 | 1ms | 1ms | 0ms |

*At time = 12,*

- Process P1 completes its execution.
- The overall execution of the processes will be as shown below:

| Time Instance | Process | Arrival Time | Ready Queue | Running Queue | Execution Time | Initial Burst Time | Remaining Burst Time |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0-2ms | P1 | 0ms | P2, P3 | P1 | 2ms | 5ms | 3ms |
| 2-4ms | P1 | 0ms | P3, P1 | P2 | 0ms | 3ms | 3ms |
|  | P2 | 1ms |  |  | 2ms | 4ms | 2ms |
| 4-6ms | P1 | 0ms | P1, P4, P2 | P3 | 0ms | 3ms | 3ms |
|  | P2 | 1ms |  |  | 0ms | 2ms | 2ms |
|  | P3 | 2ms |  |  | 2ms | 2ms | 0ms |
| 6-8ms | P1 | 0ms | P4, P2 | P1 | 2ms | 3ms | 1ms |
|  | P2 | 1ms |  |  | 0ms | 2ms | 2ms |
| 8-9ms | P1 | 0ms | P2, P1 | P4 | 0ms | 3ms | 1ms |
|  | P2 | 1ms |  |  | 0ms | 2ms | 2ms |
|  | P4 | 4ms |  |  | 1ms | 1ms | 0ms |
| 9-11ms | P1 | 0ms | P1 | P2 | 0ms | 3ms | 1ms |
|  | P2 | 1ms |  |  | 2ms | 2ms | 0ms |
| 11-12ms | P1 | 0ms |  | P1 | 1ms | 1ms | 0ms |

*Gantt chart* will be as following below:

![https://media.geeksforgeeks.org/wp-content/uploads/20220501232816/UntitledDiagram6-300x54.jpg](https://media.geeksforgeeks.org/wp-content/uploads/20220501232816/UntitledDiagram6-300x54.jpg)

https://media.geeksforgeeks.org/wp-content/uploads/20220501232816/UntitledDiagram6-300x54.jpg

Gantt chart for Round Robin Scheduling Algorithm

### *How
to compute below times in Round Robin using a program?*

- *Completion Time:* Time at which process completes its
execution.
- *Turn Around Time:* Time Difference between completion time
and arrival time. *Turn Around Time = Completion Time – Arrival
Time*
- *Waiting Time(W.T):* Time Difference between turn around time
and burst time. *Waiting Time = Turn Around Time – Burst
Time*

Now, lets calculate average [**waiting
time and turn around**](https://www.geeksforgeeks.org/difference-between-turn-around-time-tat-and-waiting-time-wt-in-cpu-scheduling/) time:

| Processes | AT | BT | CT | TAT | WT |
| --- | --- | --- | --- | --- | --- |
| P1 | 0 | 5 | 12 | 12-0 = 12 | 12-5 = 7 |
| P2 | 1 | 4 | 11 | 11-1 = 10 | 10-4 = 6 |
| P3 | 2 | 2 | 6 | 6-2 = 4 | 4-2 = 2 |
| P4 | 4 | 1 | 9 | 9-4 = 5 | 5-1 = 4 |

Now,

> Average Turn around time = (12 + 10 + 4 + 5)/4 = 31/4 = 7.7Average
waiting time = (7 + 6 + 2 + 4)/4 = 19/4 = 4.7
> 

*Example 2:* Consider the following table of arrival time and
burst time for three processes P1, P2 and P3 and given *Time Quantum
= 2*

| Process | Burst Time | Arrival Time |
| --- | --- | --- |
| P1 | 10 ms | 0 ms |
| P2 | 5 ms | 0 ms |
| P3 | 8 ms | 0 ms |

Similarly, *Gantt chart* for this example:

![https://media.geeksforgeeks.org/wp-content/uploads/20220501233833/UntitledDiagram8-300x31.jpg](https://media.geeksforgeeks.org/wp-content/uploads/20220501233833/UntitledDiagram8-300x31.jpg)

https://media.geeksforgeeks.org/wp-content/uploads/20220501233833/UntitledDiagram8-300x31.jpg

Gantt chart for example 2

Now, lets calculate average [**waiting
time and turn around**](https://www.geeksforgeeks.org/difference-between-turn-around-time-tat-and-waiting-time-wt-in-cpu-scheduling/) time:

| Processes | AT | BT | CT | TAT | WT |
| --- | --- | --- | --- | --- | --- |
| P1 | 0 | 10 | 23 | 23-0 = 23 | 23-10 = 13 |
| P2 | 0 | 5 | 15 | 15-0 = 15 | 15-5 = 10 |
| P3 | 0 | 8 | 21 | 21-0 = 21 | 21-8 = 13 |

> Total Turn Around Time = 59 msSo, Average Turn Around Time = 59/3 =
19.667 msAnd, Total Waiting Time = 36 msSo, Average Waiting Time = 36/3
= 12.00 ms
> 

## priority scheduling:

[priority scheduling code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/priority%20scheduling%20code%20b29dcbc88f4348b19e3d18b225559659.md)

[priority scheduling code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/priority%20scheduling%20code%20b29dcbc88f4348b19e3d18b225559659.md)

**Concept:**

- Processes are assigned priorities based on certain criteria
(e.g., importance, urgency, resource requirements).
- The process with the highest priority is selected to run next.
- Ensures that more important or time-sensitive tasks receive
preferential treatment.

**Key Features:**

- **Preemptive:** Higher-priority processes can interrupt
lower-priority ones.
- **Non-preemptive:** Processes run to completion before
switching, even if a higher-priority process arrives.
- **Dynamic priority:** Priorities can change based on
system events or resource usage.
- **Static priority:** Priorities remain fixed throughout
execution.

**Types:**

- **Non-preemptive Priority Scheduling:**
    - Simple implementation.
    - Can lead to starvation for lower-priority processes.
- **Preemptive Priority Scheduling:**
    - Reduces starvation but increases overhead due to context
    switching.
- **Priority with Aging:**
    - Gradually increases priority of waiting processes to prevent
    indefinite waiting.
- **Shortest Job First (SJF) with Priority:**
    - Combines priority with SJF, prioritizing both importance and burst
    time.
- **Priority with Round Robin:**
    - Prevents starvation by using time slices for each priority
    level.

**Advantages:**

- Improves responsiveness for high-priority tasks.
- Reduces waiting time for important processes.
- Efficiently manages time-sensitive operations.

**Disadvantages:**

- Potential for starvation of low-priority processes.
- Increased overhead due to context switching in preemptive
versions.
- Determining appropriate priority assignment can be challenging.

**Common Use Cases:**

- Real-time systems where deadlines are critical (e.g., flight
control, medical devices).
- Operating systems managing multiple applications with varying
importance.
- Task scheduling in servers and multi-process systems.

**Additional Considerations:**

- **Priority Inversion:** A lower-priority process
holding a resource needed by a higher-priority process can lead to
delays.
- **Starvation Avoidance:** Techniques like aging and
priority boosting help prevent indefinite waiting.
- **Overhead:** Context switching costs in preemptive
priority scheduling must be balanced with responsiveness benefits.

## multilevel queue scheduling:

[multilevel queue code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/multilevel%20queue%20code%20807dd306eaa6449796438862e3677866.md)

[multilevel queue code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/multilevel%20queue%20code%20807dd306eaa6449796438862e3677866.md)

![https://media.geeksforgeeks.org/wp-content/uploads/multilevel-queue-schedueling-1-300x217.png](https://media.geeksforgeeks.org/wp-content/uploads/multilevel-queue-schedueling-1-300x217.png)

https://media.geeksforgeeks.org/wp-content/uploads/multilevel-queue-schedueling-1-300x217.png

Multilevel Queue Scheduling (MLQ) is an algorithm used in operating
systems to manage processes with different priorities. It divides the
ready queue (where processes waiting for CPU allocation reside) into
multiple levels based on certain criteria like priority, memory usage,
or execution time. This allows the system to allocate CPU time more
efficiently and fairly according to the importance of each process.

## multilevel feedback queue
scheduling:

[multilevel feedback queue code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/multilevel%20feedback%20queue%20code%20a08cda16b20441f991a8b201722fe4c4.md)

[multilevel feedback queue code ](scheduling%20algorithm%200fdef1438b4d402d905e76a419da8a6a/multilevel%20feedback%20queue%20code%20a08cda16b20441f991a8b201722fe4c4.md)

![https://media.geeksforgeeks.org/wp-content/uploads/Multilevel-Feedback-Queue-Scheduling-300x269.png](https://media.geeksforgeeks.org/wp-content/uploads/Multilevel-Feedback-Queue-Scheduling-300x269.png)

https://media.geeksforgeeks.org/wp-content/uploads/Multilevel-Feedback-Queue-Scheduling-300x269.png

Multilevel Feedback Queue Scheduling (MLFQ) is an advanced form of
Multilevel Queue Scheduling that builds upon its core principles and
adds dynamic priority adjustments based on process behavior.

In operating systems, MLFQ is a CPU scheduling algorithm known for
its balance between fairness and efficiency. It leverages multiple
queues with priorities and adjusts process priorities dynamically based
on their CPU usage patterns. This dynamic nature makes it well-suited
for handling diverse workloads.