# Garbage Collection Strategies

Garbage Collection (GC) is an automatic memory management technique. There are several strategies for garbage collection, each with its own advantages and disadvantages, but we will focus on three main strategies: Mark-Sweep, Copying, and Mark-Compact.

## Mark-Sweep

The Mark-Sweep strategy works in two phases. The **Mark** phase traverses the object graph, starting from the root objects (objects directly accessible by the program), marking each object it reaches. The **Sweep** phase then goes through the whole heap, reclaiming the unmarked objects.

```java
System.gc(); // invokes the garbage collector in Java
```

## Copying

In the Copying strategy, the heap is divided into two equal-sized spaces. Only one space is used for allocation at a time. When the space becomes full, the live objects are copied into the other space, and the original space is then considered free.

```csharp
GC.Collect(); // invokes the garbage collector in C#
```

## Mark-Compact

The Mark-Compact strategy is a variation of Mark-Sweep. It also uses the marking phase, just like Mark-Sweep, but instead of the sweeping phase, it compacts the live objects at one end of the heap, eliminating the fragmentation problem.

```java
System.gc(); // invokes the garbage collector in Java
```

Each of these strategies is best suited to specific scenarios. For instance, Mark-Compact is a good choice for programs that have a high degree of object retainment, while Copying can be efficient for programs with a high object turnover rate.
