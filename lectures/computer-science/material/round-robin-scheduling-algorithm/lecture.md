# Round Robin Scheduling Algorithm

Round Robin Scheduling is a pre-emptive, time-sharing algorithm that manages system resources. Each task is assigned a fixed time slot or quantum.

In each quantum, the scheduler picks the next task in the queue, executes it, and then, if it's not completed, places it at the end of the queue. This process continues until every task is completed.

```python
def round_robin_scheduling(processes, n, burst_time, quantum):
    wt = [0] * n
    tat = [0] * n
    rem_bt = [0] * n

    for i in range(len(rem_bt)):
        rem_bt[i] = burst_time[i]
    t = 0

    while(1):
        done = True
        for i in range(n):
            if (rem_bt[i] > 0) :
                done = False
                if (rem_bt[i] > quantum) :
                    t += quantum
                    rem_bt[i] -= quantum
                else:
                    t = t + rem_bt[i]
                    wt[i] = t - burst_time[i]
                    rem_bt[i] = 0
        if (done == True):
            break
```

In this Python example, `round_robin_scheduling` takes four parameters: a list `processes` of n processes, their `burst_time`, and the `quantum` time. The function calculates the waiting time (`wt`) and turnaround time (`tat`) for each process.

The time complexity of this algorithm is O(n), as it loops over each process once per quantum until all processes are finished. However, the context-switching overhead can be significant if the quantum time is too small.

Despite this, Round Robin is popular due to its simplicity and fairness, ensuring no process is starved of resources for too long.
