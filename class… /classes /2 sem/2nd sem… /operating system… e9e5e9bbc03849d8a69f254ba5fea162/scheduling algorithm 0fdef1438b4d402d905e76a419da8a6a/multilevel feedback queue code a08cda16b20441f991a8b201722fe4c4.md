# multilevel feedback queue code

# multilevel feedback queue
code

```java
import java.util.*;
public class MultilevelFeedbackQueueScheduling {
    private static final int MAX_PRIORITY = 3;
    private List<Queue<Process>> queues;
    public MultilevelFeedbackQueueScheduling() {
        queues = new ArrayList<>();
        for (int i = 0; i < MAX_PRIORITY; i++) {
            queues.add(new LinkedList<>());
        }
    }
    public void addProcess(Process process) {
        queues.get(process.getPriority()).add(process);
    }
    public Process getNextProcess() {
        for (int i = 0; i < MAX_PRIORITY; i++) {
            Queue<Process> queue = queues.get(i);
            if (!queue.isEmpty()) {
                return queue.poll();
            }
        }
        return null;
    }
    public static void main(String[] args) {
        MultilevelFeedbackQueueScheduling scheduler = new MultilevelFeedbackQueueScheduling();
        // Add some processes to the scheduler
        scheduler.addProcess(new Process(1, 10));
        scheduler.addProcess(new Process(2, 5));
        scheduler.addProcess(new Process(3, 2));
        // Get the next process to run
        Process process = scheduler.getNextProcess();
        while (process != null) {
            // Run the process
            process.run();
            // Get the next process to run
            process = scheduler.getNextProcess();
        }
    }
}
class Process {
    private int id;
    private int burstTime;
    private int priority;
    public Process(int id, int burstTime, int priority) {
        this.id = id;
        this.burstTime = burstTime;
        this.priority = priority;
    }
    public int getId() {
        return id;
    }
    public int getBurstTime() {
        return burstTime;
    }
    public int getPriority() {
        return priority;
    }
    public void run() {
        System.out.println("Running process " + id);
        burstTime--;    
	}
}
```

need=max-allocation;

need≤ work ;

work=work + allocation;