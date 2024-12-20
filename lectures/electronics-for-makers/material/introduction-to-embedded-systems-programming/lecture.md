# Introduction to Embedded Systems Programming

Embedded Systems Programming refers to the practice of designing and coding software for devices that are not traditional computers. These include microcontroller-based systems and real-time systems found in a wide range of applications from cars to medical devices.

## Microcontrollers

At the heart of most embedded systems is a microcontroller. This is a simple computer on a single integrated circuit designed to control a specific task or tasks. Microcontrollers have their own memory, processing unit, and peripherals.

Example of a microcontroller is the Arduino, which is programmed using a language based on C/C++. Here's a simple Arduino code snippet for blinking an LED:

```cpp
void setup() {
  pinMode(13, OUTPUT);  // initialize digital pin 13 as an output.
}

void loop() {
  digitalWrite(13, HIGH);   // turn the LED on
  delay(1000);              // wait for a second
  digitalWrite(13, LOW);    // turn the LED off
  delay(1000);              // wait for a second
}
```

## Real-Time Systems

A real-time system is a type of embedded system that must respond to events or inputs within a specific time frame. This timing aspect is crucial, especially in safety-critical systems like an airbag deployment system in a car.

Real-time systems are often programmed in languages like C and C++, or in specialized languages like Ada for high-integrity systems. They typically incorporate a real-time operating system (RTOS) to manage task scheduling and system resources.

## Multithreading and Concurrency

Embedded systems often need to perform multiple tasks concurrently. This is achieved through multithreading, where the system switches between tasks to give the illusion of parallel processing.

In C, you can use libraries like `pthreads` to implement multithreading. Here's an example of creating two threads:

```c
#include <pthread.h>

void* print_message(void* ptr) {
  char* message;
  message = (char*) ptr;
  printf("%s \n", message);
}

int main() {
  pthread_t thread1, thread2;
  char* message1 = "Thread 1";
  char* message2 = "Thread 2";

  pthread_create(&thread1, NULL, print_message, (void*) message1);
  pthread_create(&thread2, NULL, print_message, (void*) message2);

  pthread_join(thread1, NULL);
  pthread_join(thread2, NULL);

  return 0;
}
```

This thread creation and synchronization are fundamental concepts in embedded systems programming, enabling efficient and predictable execution of tasks.