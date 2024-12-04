# Deadlock Avoidance Techniques

Deadlock is a situation where two or more processes are unable to proceed because each is waiting for the other to release resources. Deadlock avoidance aims to prevent this from happening. We'll explore two main deadlock avoidance techniques: Banker's algorithm and Resource allocation graph algorithm.

## Banker's Algorithm

Banker’s algorithm is a deadlock avoidance method which tests for safety by simulating the allocation of predetermined maximum possible amounts of all resources, then makes an "s-state" check to test for possible deadlock conditions for all other pending activities, before deciding whether allocation should be allowed to continue.

The Banker's algorithm follows these steps:

1. When a new process enters the system, it must declare the maximum number of instances of each resource type that it may need.
2. When a process requests resources, the system checks if granting the request will maintain the system in a safe state. If it does, the resources are allocated; if it doesn't, the process must wait until other processes release resources.

```python
# Python code representing a simplified Banker's Algorithm
def isSafe(processes, avail, maxm, allot):
    need = calculateNeed(maxm, allot)
    finish, safeSeq = initializeVars(processes)

    # While all processes are not finished
    while(countUnfinishedProcesses(finish) != 0):
        safe = False

        # Find a process which can be allocated all its remaining resources
        for p in range(len(processes)):
            if (isProcessSafe(p, need, finish, avail)):
                safeSeq.append(p)
                safe = True

        # If no process can be allocated, deadlock is possible
        if (not safe):
            print("System is not in safe state")
            return False

    print("System is in safe state.\nSafe sequence is: ", end = "")
    print(*safeSeq)
    return True
```

## Resource Allocation Graph (RAG) Algorithm

Another deadlock avoidance method is the Resource Allocation Graph (RAG) algorithm. This represents each process and resource as a graph, with directed edges connecting processes to resources.

In RAG, if a process requests resources that are currently held by another process, a directed edge from the resource to the requesting process is added. If granting the request results in no circular wait, the resources are allocated to the requesting process.

```python
# Python code representing a simplified RAG Algorithm
def detectDeadlock(processes, resources, edges):
    graph = makeGraph(processes, resources, edges)
    if containsCycle(graph):
        print("System is in deadlock")
    else:
        print("No deadlock detected")
```

These are two techniques for avoiding deadlock. Both of these techniques require knowledge about future process requests, which is generally not possible in most real-world scenarios. However, understanding these techniques is important for understanding the principles of deadlock avoidance.