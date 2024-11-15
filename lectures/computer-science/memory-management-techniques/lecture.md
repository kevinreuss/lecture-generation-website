# Memory Management Techniques

Memory management is a crucial aspect of software engineering, particularly in lower-level programming languages like C and C++, which don't provide garbage collection out of the box. Let's dive into two important techniques: Static and Dynamic Memory Allocation.

## Static Memory Allocation

In static memory allocation, all the memory needed by an application is determined at compile-time. Let's look at a simple C code example:

```C
int main() {
    int array[100];
    return 0;
}
```

In this example, an array of 100 integers is statically allocated in the stack. The size of this array is fixed and can't be changed at runtime.

## Dynamic Memory Allocation

In contrast, dynamic memory allocation permits variable allocation of memory during runtime. Here's an example in C using the `malloc` function:

```C
int main() {
    int *array = (int*) malloc(100 * sizeof(int));
    free(array);
    return 0;
}
```

Here, an array of 100 integers is dynamically allocated in the heap. The size of the array can be changed at runtime, and it's crucial to manually deallocate the memory using `free` to prevent memory leaks.

## Automatic Garbage Collection

Automatic garbage collection, provided by languages like Java and Python, automatically reclaims memory that the garbage collector determines is no longer in use. However, it comes with a performance cost.

```Java
public class Main {
    public static void main(String[] args) {
        int[] array = new int[100];
    }
}
```

In this Java example, an array of 100 integers is created. The garbage collector automatically frees up memory when `array` is no longer in use.
