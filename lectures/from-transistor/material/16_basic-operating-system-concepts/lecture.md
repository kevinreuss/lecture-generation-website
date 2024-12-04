# Basic Operating System Concepts

## Process Management

Operating systems manage processes which are running instances of programs. They handle creation, scheduling, termination, and synchronization of processes. Inter-process communication (IPC) is a method that allows processes to communicate with each other and synchronize their actions.

Example:
In Unix, a process can be created with `fork()` and terminated with `exit()`. Child processes can be created as copies of the parent process.

```c
#include <stdio.h> 
#include <sys/types.h> 
#include <unistd.h> 

void forkexample() 
{ 
    if (fork() == 0) 
        printf("Hello from Child!\n"); 
    else
        printf("Hello from Parent!\n"); 
} 

int main() 
{ 
    forkexample(); 
    return 0; 
} 
```

## Memory Management

Operating systems manage the memory hierarchy which includes the management of virtual memory and physical memory. They handle allocation, deallocation and swapping of memory between these two types. 

Example:
Memory allocation in C can be done using `malloc()`, `calloc()`, `realloc()` and memory can be deallocated using `free()`.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr;
    ptr = malloc(15 * sizeof(*ptr)); /* a block of 15 integers */
    if (ptr != NULL) {
        *(ptr + 5) = 480;  /* assign 480 to sixth integer */
    }
    printf("Value of the 6th integer is %d",*(ptr + 5));
    return 0;
}
```

## File System Management

Operating systems manage the file system which includes file creation, deletion, read, write operations, as well as permission management and directory organization.

Example:
In Unix, a file can be opened with `fopen()`, written using `fwrite()`, read using `fread()`, and closed with `fclose()`.

```c
#include <stdio.h>

int main() {
    FILE *fp;
    char str[] = "This is tutorialspoint.com";

    fp = fopen("file.txt", "w");
    fwrite(str , 1 , sizeof(str) , fp );

    fclose(fp);
    return(0);
}
```

These are some of the foundational concepts of operating systems. Each of these areas is a deep field of study in its own right, with a variety of techniques and methods used to solve complex, real-world problems.