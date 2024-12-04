# Type Inference in TypeScript and Kotlin

In both TypeScript and Kotlin, type inference refers to the ability of the compiler to determine types of variables and expressions automatically.

## TypeScript Type Inference

In TypeScript, if you assign a value to a variable when declaring it, TypeScript will infer the type of the variable based on the assigned value. For example:

```typescript
let message = "Hello, World!"; // message is inferred as 'string'
```

However, TypeScript can also infer types in more complex scenarios, such as in functions. Consider the following example:

```typescript
function addNumbers(a = 0, b = 0) {
  return a + b; // TypeScript infers the return type as 'number'
}
```

In this example, TypeScript infers the return type of the `addNumbers` function to be `number`, based on the types of `a` and `b`.

## Kotlin Type Inference

Like TypeScript, Kotlin also uses type inference. When you assign a value at the declaration, Kotlin's compiler infers the variable's type. For example:

```kotlin
val message = "Hello, World!" // message is inferred as 'String'
```

Kotlin also infers types in functions. However, unlike TypeScript, Kotlin requires explicit type declaration for function parameters. The return type though, can be inferred. For example:

```kotlin
fun addNumbers(a: Int, b: Int) = a + b // Return type 'Int' is inferred
```

In this example, Kotlin infers the return type of the `addNumbers` function to be `Int`, based on the types of `a` and `b`.

In conclusion, type inference in both TypeScript and Kotlin allows for cleaner, more readable code, by reducing the need for explicit type declarations.