# Compiler Optimization Techniques

## Loop Optimization

Loop optimization is a common technique that can greatly reduce execution time. Loop unrolling, for instance, removes the overhead of loop control instructions by replicating the loop body. For example:

```cpp
for (int i = 0; i < 10; i++) { foo(); }
```

Becomes:

```cpp
foo(); foo(); foo(); foo(); foo(); foo(); foo(); foo(); foo(); foo();
```

## Constant Folding

Constant folding simplifies known constants at compile-time. For example:

```cpp
int x = 7 * 6;
```

The compiler optimizes this to:

```cpp
int x = 42;
```

## Dead Code Elimination

Dead code, or code that doesn't affect the program's outcome, is removed by this optimization.

```cpp
int x = compute(); // compute is complex function
x = 10;
```

The compiler can eliminate the call to `compute()`, as its result isn't used.

## Function Inlining

Function inlining aims to eliminate the overhead of function calls by replacing calls with the function's content.

```cpp
void foo() { /*...*/ }
void bar() { foo(); }
```

Becomes:

```cpp
void bar() { /* content of foo */ }
```

## Strength Reduction

This technique replaces expensive operations with equivalent cheaper ones. For example, multiplication by a power of two can be replaced by a left shift operation.

```cpp
int x = y * 2;
```

Becomes:

```cpp
int x = y << 1;
```

Remember, the goal of these techniques is to improve performance, but they also increase the complexity of the compiled code. Hence, they should be utilized judiciously.