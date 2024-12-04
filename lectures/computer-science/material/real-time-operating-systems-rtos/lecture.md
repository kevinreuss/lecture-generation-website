# Real-Time Operating Systems (RTOS)

A **Real-Time Operating System (RTOS)** is an operating system that guarantees a certain capability within a specified time constraint. For instance, an operating system might be designed to ensure that a certain object was available for a robot on an assembly line. In what is usually called a "hard" real-time operating system, if the calculation could not be performed for making the object available at the designated time, the system would terminate with a failure.

In a "soft" real-time operating system, the assembly line would continue to function but the production output might be lower as objects failed to appear at their designated time, causing the robot to be temporarily unproductive. Some real-time operating systems are created for a particular application and others are more general purpose.

## Key Features

- **Determinism**: The key factor of RTOS is its consistent high performance. Task execution takes place in strictly defined time constraints.

- **Multitasking**: RTOS supports multi-threaded programming, where multiple threads run concurrently.

- **Inter-task Communication**: Tasks communicate with each other through mechanisms provided by RTOS like semaphores, mailboxes, and message queues.

- **Memory Management**: RTOS provides memory management to ensure optimal use of memory resources.

Here's a simple code snippet of a task creation in FreeRTOS, a popular RTOS:

```c
#define STACK_SIZE 1000
TaskHandle_t handle = NULL;

void taskFunction(void* param) {
    while(true) {
        // Your task code here
    }
}

void setup() {
    xTaskCreate(taskFunction, "TaskName", STACK_SIZE, NULL, 1, &handle);
}
```

The above code creates a task with a stack size of 1000, priority 1, and registers it to the RTOS scheduler. The task continuously runs the code defined in `taskFunction`.

## Scheduling Algorithms

RTOS typically use one of the following scheduling algorithms:

- **Preemptive Scheduling**: An ongoing task is interrupted when a higher priority task enters a ready state.

- **Round Robin Scheduling**: Each task is assigned a fixed time slot, in a cyclic way.

- **Priority Scheduling**: Tasks are scheduled based on their priority. The task with the highest priority is executed first.

RTOS are critical in systems where time constraints must be met, like in medical equipment, aviation, telecommunications, and real-time simulations.
