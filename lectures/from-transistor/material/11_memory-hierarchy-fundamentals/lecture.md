# Memory Hierarchy Fundamentals

Memory hierarchy is a crucial concept in computer architecture. It refers to the arrangement of storage types based on speed, cost, and size. The hierarchy includes registers, cache, main memory, and secondary storage. 

**Registers** are the fastest and most expensive type of memory. They are integrated directly into the CPU and used to store data currently in use.

```C
int x = 10;  // The value 10 is stored in a register
```

**Cache** memory, subdivided into L1, L2, and L3 caches, is slower and cheaper than registers but faster and more expensive than main memory. It is used to store frequently accessed data to reduce access time.

```C
int array[1000];
int sum = 0;
for (int i = 0; i < 1000; i++) {
    sum += array[i];  // Elements of array will be stored in cache after first access
}
```

**Main Memory (RAM)** is slower and cheaper than cache. It is used to store data and instructions currently in use. 

```C
int* ptr = (int*) malloc(1000 * sizeof(int));  // Allocates memory in RAM
```

**Secondary Storage (Hard Disk, SSD)** is the slowest and cheapest type of memory. It is used to store data not currently in use.

```C
FILE* file = fopen("data.txt", "r");  // Reads data from secondary storage
```

The hierarchy is organized such that as one goes down the hierarchy, the memory gets slower but larger and less expensive. The goal of the memory hierarchy is to provide the CPU with data as quickly as possible while keeping the overall cost of the computer system within reasonable limits.