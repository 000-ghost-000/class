# first come first serve code

# first come first serve code

```java
import java.util.LinkedList;
import java.util.Queue;
public class FcfsScheduler {    
private Queue<Process> queue;    
public FcfsScheduler() {        
this.queue = new LinkedList<>();    
} 
   public void addProcess(Process process) {
        queue.add(process);    }    
public void schedule() {        
while (!queue.isEmpty()) {
            Process currentProcess = queue.poll();
            currentProcess.execute();
        }
    }    // Define the Process class with attributes like processID, arrivalTime, burstTime, and methods like execute()}
```