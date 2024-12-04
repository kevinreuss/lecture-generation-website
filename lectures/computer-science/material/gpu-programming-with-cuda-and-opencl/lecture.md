# GPU Programming with CUDA and OpenCL

## **CUDA Programming**

**CUDA** (Compute Unified Device Architecture) is a parallel computing platform and API model created by NVIDIA. It allows software developers to use a CUDA-enabled graphics processing unit (GPU) for general purpose processing.

Here's a basic example of a CUDA program that adds two arrays in parallel:

```c
__global__ void add(int *a, int *b, int *c, int n) {
    int index = threadIdx.x + blockIdx.x * blockDim.x;
    if (index < n)
        c[index] = a[index] + b[index];
}

int main() {
    // Code for initializing arrays a, b and c...

    // Perform array addition on GPU
    add<<<N,1>>>(d_a, d_b, d_c, N);

    // Code for copying the result back to host and cleaning up...
}
```

The `add` function is a **kernel**, a function that runs on the GPU. The `<<<N,1>>>` syntax is used to specify the execution configuration, telling CUDA to use N parallel threads.

## **OpenCL Programming**

**OpenCL** (Open Computing Language) is a framework for writing programs that execute across heterogeneous platforms consisting of CPUs, GPUs, and other processors. OpenCL includes a language (based on C99) for writing kernels and APIs that are used to define and control platforms.

Here's a similar example to the CUDA one, but in OpenCL:

```c
__kernel void add(__global int* a, __global int* b, __global int* c) {
    int index = get_global_id(0);
    c[index] = a[index] + b[index];
}

int main() {
    // Code for setting up OpenCL context, command queue, and memory buffers...

    // Build and execute the kernel
    clEnqueueNDRangeKernel(queue, kernel, 1, NULL, &global_size, &local_size, 0, NULL, NULL);

    // Code for reading the result back to host and cleaning up...
}
```

The `add` function is again a **kernel**. `clEnqueueNDRangeKernel` function is used to execute the kernel over the entire range of the data set in parallel.

Both CUDA and OpenCL provide a significant increase in performance by exploiting parallelism, a key factor in modern computing. However, each has its own advantages and trade-offs in terms of portability, performance, and ease-of-use.
