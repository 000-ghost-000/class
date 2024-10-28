# shortest job first code

# shortest job first code

```java
import java.util.*;
public class SJFScheduler {
    private PriorityQueue<Process> queue;
 // Use PriorityQueue for sorting by burst time
    public SJFScheduler() {
        this.queue = new PriorityQueue<>((p1, p2) -> Integer.compare(p1.getBurstTime(), p2.getBurstTime()));
 // Burst time as priority
    }
    public void addProcess(Process process) {
        queue.add(process);
    }
    public void schedule() {
        while (!queue.isEmpty()) {
            Process currentProcess = queue.poll();
 // Get the shortest job
            currentProcess.execute();
            if (!currentProcess.isFinished()) {
                // Re-add uncompleted processes in non-preemptive cases
                if (!currentProcess.isPreemptive()) {
                    throw new UnsupportedOperationException("Non-preemptive SJF not supported");
                }
 else {
                    queue.add(currentProcess);
 // Add back for next round
                }
            }
        }
    }
    // Define the Process class with attributes like processID, arrivalTime, burstTime, isPreemptive, and methods like execute(), isFinished()}
```