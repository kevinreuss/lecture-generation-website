# Process Management Basics

Process management is a key aspect of operating systems, dealing with the creation, scheduling, termination, and coordination of processes. 

## Process Creation

Processes can be created by other processes through system calls such as `fork()`. The child process inherits properties from its parent and executes concurrently with the parent.

```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
    fork();
    printf("Hello World\n");
    return 0;
}
```
In this example, 'Hello World' is printed twice because the `fork()` call creates a new process that also executes the `printf()` statement.

## Process States

A process can be in one of the following states:

- **New:** The process is being created.
- **Running:** Instructions are being executed.
- **Waiting:** The process is waiting for some event to occur.
- **Ready:** The process is waiting to be assigned to a processor.
- **Terminated:** The process has finished execution.

## Process Control Block (PCB)

Each process is represented in the operating system by a process control block (PCB), also known as a task control block. It contains important information about the specific process including:

- **Process State:** The state of the process (as described above).
- **Program Counter:** The address of the next instruction to be executed for this process.
- **CPU Registers:** They include accumulators, index registers, stack pointers, and general-purpose registers, plus any condition-code information.

## Process Scheduling

The operating system schedules processes based on a particular algorithm like First-Come-First-Serve (FCFS), Shortest Job Next (SJN), or Round Robin (RR). The choice of the scheduling algorithm impacts the process performance.

## Process Termination

A process terminates when it finishes executing its final statement and asks the operating system to delete it with the `exit()` system call. Alternatively, a process can be killed by another using a `kill()` system call.
```
kill(pid, SIGKILL);
```
In this example, the `kill()` function sends the `SIGKILL` signal to the process with the process ID `pid`, causing that process to terminate immediately.
