# priority scheduling code

# priority scheduling code

```java
import java.util.*;
public class PriorityScheduler {
    private PriorityQueue<Process> queue;
 // Use PriorityQueue for priority-based sorting
    public PriorityScheduler() {
        this.queue = new PriorityQueue<>((p1, p2) -> Integer.compare(p2.getPriority(), p1.getPriority()));
 // Higher priority first
    }
    public void addProcess(Process process) {
        queue.add(process);
    }
    public void schedule() {
        while (!queue.isEmpty()) {
            Process currentProcess = queue.poll();
 // Get the highest priority process
            currentProcess.execute();
            if (!currentProcess.isFinished()) {
                // Re-add only if non-preemptive and not finished
                if (!currentProcess.isPreemptive()) {
                    queue.add(currentProcess);
                }
            }
        }
    }
    // Define the Process class with attributes like arrivalTime, burstTime, priority, isPreemptive, and methods like execute(), isFinished()}
```