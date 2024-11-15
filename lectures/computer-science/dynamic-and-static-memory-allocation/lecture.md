# Dynamic and Static Memory Allocation

## Static Memory Allocation

In static memory allocation, the size and type of the allocated memory are known at compile time. The memory is allocated on the stack and deallocated automatically when it goes out of scope. Below is a simple example in C:

```c
int myArray[20]; // static memory allocation
```

In this case, `myArray` allocates 20 integers worth of memory on the stack when it is declared. This block of memory will be automatically freed when `myArray` goes out of scope.

## Dynamic Memory Allocation

Dynamic memory allocation, on the other hand, allows you to allocate memory during runtime. The allocated memory resides in the heap and must be managed manually. This means you have to deallocate it yourself when it's no longer needed, using functions like `free()` in C or `delete` in C++. Here's an example in C:

```c
int* myDynamicArray = malloc(20 * sizeof(int)); // dynamic memory allocation
...
free(myDynamicArray); // freeing dynamically allocated memory
```

In the example above, `myDynamicArray` points to a block of memory in the heap, large enough to hold 20 integers. This block of memory remains allocated until `free()` is called on it.

## Comparison

While static memory allocation is easier and safer due to automatic deallocation, it lacks flexibility. Dynamic memory allocation, however, gives you more control and allows dynamic data structures like linked lists and trees. But, it makes it easier to cause memory leaks or dangling pointers if not handled properly. 

In summary, choosing between dynamic and static memory allocation depends on your needs - static for simplicity and safety, dynamic for flexibility and control.  
