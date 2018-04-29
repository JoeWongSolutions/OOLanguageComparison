[Back to main](README.md)
# Multithreading in Java and Swift
Both Java and Swift support multithreading through inheriting the Thread class. Java supports multi-processes in order to handle concurrency but Swift does not allow multi-processes for a single application.

### Code for creating a thread in Java
```Java
public class MyThread extends Thread {

    public void run(){
       System.out.println("MyThread running");
    }
}
MyThread myThread = new MyThread();
myTread.start();
```
### Alternative to inheriting from Thread is to implement the Runnable class
```Java
public class MyRunnable implements Runnable {

    public void run(){
       System.out.println("MyRunnable running");
    }
}
Thread thread = new Thread(new MyRunnable());
thread.start();
```

### Code for creating a thread in Swift
```Swift
class MyThread: Thread {
  override func main() {
    do_something
  }
}

let myThread = MyThread()
myThread.start()
```

# How is multitasking accomplished?
In Java, we can only rely on multiple processes or threads to run tasks concurrently. In Swift, and in particular when developing for IOS, Processes are limited to 1 per application and threads are limited to 64 concurrent threads. So what if we need more? Swift supports the idea of having dispatch queues. Dispatch queues are a way to turn threads into task queues that can have tasks pushed into the queue for eventual handling. 
```Swift
DispatchQueue.main.async {
    // execute async on main thread
}
```
This code would allow us to throw tasks into the main thread asynchronously so we know that they will eventually be handled. But how is this multithreading? We can have more than one dispatch queue! This is how we create an OperationQueue:
```Swift
let operationQueue: OperationQueue = OperationQueue()
operationQueue.addOperations([operation1], waitUntilFinished: false)
```
Operation Queues are threads that run concurrently with the main thread and can also have tasks pushed into the queue for eventual handling. By using multiple operation queues, Swift allows developers to better utilize the resources on the device when multithreading.
[Back to main](README.md)
