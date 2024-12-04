# Code Optimization Basics

When we talk about **Code Optimization**, we are fundamentally discussing two primary aspects: **Performance Optimization** and **Memory Optimization**. 

## Performance Optimization

Performance optimization aims at reducing the execution time of your code. 

### Loop Unrolling 

Consider this loop:

```c++
for(int i = 0; i < 100; i++){
    // Some operation
}
```
Loop unrolling would transform this to:
```c++
for(int i = 0; i < 100; i+=10){
    // Operation 1
    // Operation 2
    // Operation 3
    // ...
    // Operation 10
}
```
This reduces the overhead of loop counter increment and condition check.

### Function Inlining 

Function calls can be expensive in terms of time. Instead, if the function body is small, the function call can be replaced with the function body. This is known as **Function Inlining**.

```c++
inline void fun() {
    // Small amount of code
}
```
The `inline` keyword suggests to the compiler that it should attempt to embed this function's code in place of any call to it.

## Memory Optimization

Memory optimization is about reducing your program's memory footprint.

### Variable Reuse

Reusing variables can save memory. Instead of creating a new variable every time, try to use the existing ones.

```c++
int res = doSomething();
// Some code where res is not used
res = doSomethingElse();
```

### Efficient Data Structures

Efficient use of data structures can greatly reduce memory usage. For instance, using bit fields in a structure or using an `enum` instead of a string for state management.

Remember, these are the basics. Code optimization is a vast topic and can get very complex depending on the language, platform, and problem at hand.