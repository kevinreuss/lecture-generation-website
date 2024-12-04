# SIMD Optimization for High-Performance Code

SIMD (Single Instruction, Multiple Data) is a class of parallel computers that performs the same operation on multiple data points simultaneously. It is instrumental in optimizing code for high performance.

### Vectorization

SIMD is a type of vectorization, where operations are applied to arrays or vectors instead of individual scalars. This leverages data level parallelism.

Consider the following C++ code for adding two arrays:

```cpp
for (int i = 0; i < N; ++i) 
    c[i] = a[i] + b[i];
```

We can vectorize this using SIMD instructions:

```cpp
for (int i = 0; i < N; i += 4) 
    _mm_storeu_ps(&c[i], _mm_add_ps(_mm_loadu_ps(&a[i]), _mm_loadu_ps(&b[i])));
```

### Intrinsic Functions

Intrinsic functions are used to directly utilize SIMD operations, providing more control over the process. They are specific to compiler and hardware, so portability can be an issue.

### Loop Unrolling

Loop unrolling can decrease the overhead of loop control mechanisms by increasing the granularity of the computations. 

For instance, the first example can be unrolled as:

```cpp
for (int i = 0; i < N; i += 4) {
    c[i] = a[i] + b[i];
    c[i+1] = a[i+1] + b[i+1];
    c[i+2] = a[i+2] + b[i+2];
    c[i+3] = a[i+3] + b[i+3];
}
```

### Alignment

Data alignment is crucial for maximizing SIMD performance. Data should be aligned to the natural boundaries of the SIMD unit size. 

### Compiler Directives

Compiler directives like `#pragma simd` can be used to hint the compiler about potential vectorization opportunities. However, the directives might not be portable.

### Limitations

SIMD requires uniformity of data and operations. Also, data dependencies can inhibit vectorization. Therefore, it is not always a fit for all scenarios, but when it does, it can significantly boost performance.