# Multi-Threaded Programming in Java

Java provides built-in support for multi-threaded programming. A thread in Java is a lightweight, independent unit of execution that consists of a set of instructions.

## Creating a Thread

There are two ways to create a thread in Java:

1. By extending the `Thread` class
2. By implementing the `Runnable` interface

### Extending the Thread class

```Java
class MyThread extends Thread {
    public void run(){
        // code for the thread to execute
    }
}

public class Main {
    public static void main(String[] args){
        MyThread t = new MyThread();
        t.start(); // Starts the execution of the new thread
    }
}
```

### Implementing Runnable Interface

```Java
class MyRunnable implements Runnable {
    public void run(){
        // code for the thread to execute
    }
}

public class Main {
    public static void main(String[] args){
        Thread t = new Thread(new MyRunnable());
        t.start(); // Starts the execution of the new thread
    }
}
```

## Thread States

A thread in Java can be in one of the following states:

- NEW: A thread that has not yet started is in this state.
- RUNNABLE: A thread executing in the Java virtual machine is in this state.
- BLOCKED: A thread that is blocked waiting for a monitor lock is in this state.
- WAITING: A thread that is waiting indefinitely for another thread to perform a particular action is in this state.
- TIMED_WAITING: A thread that is waiting for another thread to perform an action for up to a specified waiting time is in this state.
- TERMINATED: A thread that has exited is in this state.

## Synchronization

Synchronization in Java is the capability to control the access of multiple threads to shared resources. Without synchronization, one thread can modify a shared object while another thread is in the process of using or updating the object's value. This often leads to significant errors.

```Java
class Counter{
    private int count = 0;

    // Synchronized method to increase count
    public synchronized void increment(){
        count++;
    }

    public int getCount(){
        return count;
    }
}
```
In the above example, the `increment()` method is synchronized. This means that if multiple threads call this method on the same `Counter` object, the method will be executed by one thread at a time.