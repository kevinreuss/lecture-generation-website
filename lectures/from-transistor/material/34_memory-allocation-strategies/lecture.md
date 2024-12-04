# Memory Allocation Strategies

Memory allocation strategies are crucial for managing system resources efficiently. They determine how memory is assigned to processes, handling fragmentation, and ensuring optimal performance.

## Static vs Dynamic Memory Allocation

**Static Memory Allocation** happens at compile time. The memory size is known beforehand and doesn't change during program execution. An example of this is an array declaration in C:

```c
int array[20];
```

**Dynamic Memory Allocation** occurs at runtime. The memory size can change during program execution. It's used when the exact memory needed isn't known in advance. An example in C using `malloc`:

```c
int *array = (int*) malloc(20 * sizeof(int));
```

## Memory Allocation Techniques

### First Fit

First Fit allocates the first block of memory where the process fits. It's quick but can lead to external fragmentation.

```c
// Example of First Fit
void *firstFit(size_t size) {
  struct block *curr = head;
  while(curr) {
    if(curr->size >= size){
      return curr;
    }
    curr = curr->next;
  }
  return NULL;  // no suitable block found
}
```

### Best Fit

Best Fit searches the whole list and allocates the smallest block of memory that satisfies the request. It minimizes wasted space but is slower as it needs to traverse the entire list.

```c
// Example of Best Fit
void *bestFit(size_t size) {
  struct block *curr = head;
  struct block *bestSoFar = NULL;  // keep track of the best fit
  while(curr) {
    if(curr->size >= size && (!bestSoFar || curr->size < bestSoFar->size)){
      bestSoFar = curr;
    }
    curr = curr->next;
  }
  return bestSoFar;  // return the best fit found
}
```

### Worst Fit

Worst Fit allocates the largest block of memory. This strategy aims to leave the largest possible contiguous space free after allocation. 

```c
// Example of Worst Fit
void *worstFit(size_t size) {
  struct block *curr = head;
  struct block *worstSoFar = NULL;  // keep track of the worst fit
  while(curr) {
    if(curr->size >= size && (!worstSoFar || curr->size > worstSoFar->size)){
      worstSoFar = curr;
    }
    curr = curr->next;
  }
  return worstSoFar;  // return the worst fit found
}
```

Understanding these strategies and their trade-offs allows for better control of memory management, leading to more efficient and performant software.