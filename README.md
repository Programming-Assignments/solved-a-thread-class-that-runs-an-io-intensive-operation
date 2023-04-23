Download Link: https://assignmentchef.com/product/solved-a-thread-class-that-runs-an-io-intensive-operation
<br>
.

a) The IO bound class will be a thread class that runs an IO intensive operation. You can write to the system out a number of times (ie 1000) or do something like read and write a file.

b) The processor bound class will be a thread class that runs a computationally intensive operation. You can perform some math computation a number of times. No IO in the loop.

c) Create a controller class that implements an FCFS schedule and instantiates 5 objects of each class and runs each object.

2) Take the start and stop time for each thread and print out the time it takes to run.

3) Take the start and stop time to schedule and run all the threads and print out the time to run.

4) Run the program 3 times.

a) First time intersperse the IO bound and computationally intensive operations (call the start method).

b) Second time run the IO bound threads first and the processor bound second.

c) Third time run the processor bound threads first and the IO bound second.

5) Attach your code as well as a document. The document should include snapshots (enough to demonstrate it ran) of the running code as well as results in spreadsheet form. Results should also list the wait time for each thread. Also calculate for each of the 3 scenarios the average wait time for the

IO bound threads, processor bound threads and the overall run time for all of the threads. Include a lessons learned contrasting how the Java environment handled the 3 scenarios.

public class ComputationalOperation implements Runnable {

private Thread t;private String threadName;private long sum;

/***** @param name*/ComputationalOperation(String name) {threadName = name;

}

public void run() {try {for (int i = 0; i &lt; 20; i++) {sum += i;Thread.sleep(50);}} catch (InterruptedException e) {System.out.println(“Thread ” + threadName + ” interrupted.”);}System.out.println(“Sum ” + sum);}

public void start() {if (t == null) {t = new Thread(this, threadName);t.start();}}

}

public class Controller {/***** @param args*/public static void main(String args[]) {IntensiveOperation i1 = new IntensiveOperation(“I1”);i1.start();IntensiveOperation i2 = new IntensiveOperation(“I2”);i2.start();IntensiveOperation i3 = new IntensiveOperation(“I3”);i3.start();

ComputationalOperation c1 = new ComputationalOperation(“C1”);c1.start();

}}

public class IntensiveOperation implements Runnable {

private Thread t;private String threadName;

IntensiveOperation(String name) {threadName = name;}

public void run() {try {for (int i = 0; i &lt; 100; i++) {System.out.println(“Thread: ” + threadName + “, ” + i);Thread.sleep(50);}} catch (InterruptedException e) {System.out.println(“Thread ” + threadName + ” interrupted.”);}System.out.println(“Thread ” + threadName + ” exiting.”);}

public void start() {System.out.println(“Starting ” + threadName);if (t == null) {t = new Thread(this, threadName);t.start();}}

}