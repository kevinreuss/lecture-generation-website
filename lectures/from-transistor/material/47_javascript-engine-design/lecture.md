# JavaScript Engine Design

A JavaScript engine is a program or interpreter which executes JavaScript code. Each web browser has its own implementation of a JavaScript engine. Examples include Google's V8 (used in Chrome and Node.js), Firefox's SpiderMonkey, and Safari's JavaScriptCore.

## Engine Components

A JavaScript engine has two main components: the Memory Heap and the Call Stack.

- The **Memory Heap** is where memory allocation happens. For instance:

```javascript
let number = 60; // Allocates memory for a number
```

- The **Call Stack** is where your function calls are formed and processed.

```javascript
function multiply(a, b) {
  return a * b;
} 
multiply(5, 12); // This function call gets added to the call stack
```

## Compilation vs Interpretation

JavaScript is both compiled and interpreted. It's known as a Just-In-Time (JIT) compiled language. The engine first compiles the JavaScript code before it's executed, which differs from languages like C or Java, where the code is compiled before running the program.

## Engine Workflow

A JavaScript engine follows these steps:

1. **Parsing:** The JavaScript engine parses the code into a data structure known as the Abstract Syntax Tree (AST).
2. **Compilation:** The code is then compiled into bytecode.
3. **Execution:** Bytecode is translated into machine code for execution.

```javascript
function sum(a, b) {
  return a + b;
} 
sum(5, 7); // The engine will parse, compile, and then execute this code
```

## Optimization

JavaScript engines use various optimization strategies to make code execution faster. One such technique is "hot function" inlining, where frequently-called functions get their bytecode inlined to reduce calling overhead.

```javascript
function square(n) {
  return n * n;
} 

for (let i = 0; i < 1000; i++) {
  square(i); // This function might be inlined due to frequent calls
}
```

Remember, the design of JavaScript engines involves many complex and intricate processes. The aforementioned points give an insight into the basic workflow and components of JavaScript engine design.