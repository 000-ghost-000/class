# round robin code

# round robin code

```java
import java.util.LinkedList;
import java.util.Queue;public class RoundRobinScheduler {
    private Queue<Process> queue;
    private final int timeQuantum;
    public RoundRobinScheduler(int timeQuantum) {
        this.queue = new LinkedList<>();
        this.timeQuantum = timeQuantum;
    }
    public void addProcess(Process process) {
        queue.add(process);
    }
    public void schedule() {
        while (!queue.isEmpty()) {
            Process currentProcess = queue.poll();
            int remainingTime = currentProcess.getBurstTime();
            int executedTime = Math.min(remainingTime, timeQuantum);
            currentProcess.execute(executedTime);
							remainingTime -= executedTime;
            if (remainingTime > 0) {
                currentProcess.setBurstTime(remainingTime);
 // Update burst time if not finished
                queue.add(currentProcess);
 // Add back to queue for next round
            }
        }
    }
    // Define the Process class with attributes like processID, arrivalTime, burstTime, and methods like execute(), getBurstTime(), and setBurstTime()}
```