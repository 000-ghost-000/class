# reader writer java code

```java
import java.util.concurrent.Semaphore;

public class ReadersWriters {
    private static int readCount = 0;
    private static Semaphore mutex = new Semaphore(1); // Mutex for critical section access
    private static Semaphore writeLock = new Semaphore(1); // Semaphore for writer access

    public static void main(String[] args) throws InterruptedException {
        Reader reader1 = new Reader();
        Reader reader2 = new Reader();
        Writer writer1 = new Writer();
        Writer writer2 = new Writer();

        reader1.start();
        reader2.start();
        writer1.start();
        writer2.start();
    }

    static class Reader extends Thread {
        @Override
        public void run() {
            while (true) {
                try {
                    // Acquire mutex to enter critical section
                    mutex.acquire();

                    // Increment read count
                    readCount++;

                    // Release mutex after entering critical section
                    mutex.release();

                    // Simulate reading for some time
                    System.out.println("Reader " + Thread.currentThread().getName() + " is reading");
                    Thread.sleep(1000);

                    // Acquire mutex to exit critical section
                    mutex.acquire();

                    // Decrement read count
                    readCount--;

                    // Release mutex after exiting critical section
                    mutex.release();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    static class Writer extends Thread {
        @Override
        public void run() {
            while (true) {
                try {
                    // Acquire write lock (exclusive access)
                    writeLock.acquire();

                    // Simulate writing for some time
                    System.out.println("Writer " + Thread.currentThread().getName() + " is writing");
                    Thread.sleep(2000);

                    // Release write lock
                    writeLock.release();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```