# Functional Programming with Haskell and Lisp

Functional programming is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids state and mutable data. Two popular languages in this paradigm are Haskell and Lisp. Let's dive into some specific aspects of these languages.

## Pure Functions in Haskell

Haskell is a statically-typed functional programming language that emphasizes on pure functions. Pure functions are those that given the same input, will always return the same output, and they don't produce any side effects.

Consider the following Haskell function:

```Haskell
double x = x * 2
```

In this case, `double` is a pure function. For a given `x`, it will always return the same result without modifying any state.

## Recursion in Haskell

Since Haskell is a functional language, it uses recursion extensively instead of loops. Here's how we could define a function to calculate factorial in Haskell:

```Haskell
factorial 0 = 1
factorial n = n * factorial (n - 1)
```

The `factorial` function calls itself recursively until it reaches the base case of `factorial 0`.

## Lisp and First-Class Functions

Lisp, specifically Common Lisp, is a dynamically-typed functional language that supports first-class functions. This means functions can be passed as arguments to other functions, returned as values from other functions, and assigned to variables.

Here's an example in Lisp of a higher order function that takes a function and a list as arguments and applies the function to each element of the list:

```Lisp
(mapcar #'(lambda (x) (* x x)) '(1 2 3 4))
```

## Lisp Recursion

Like Haskell, Lisp also relies heavily on recursion. Here's the Lisp version of the factorial function:

```Lisp
(defun factorial (n)
  (if (<= n 1)
      1
      (* n (factorial (- n 1)))))
```

This `factorial` function works similarly to the Haskell version, calling itself recursively until it reaches the base case.

## Conclusion

Both Haskell and Lisp exemplify key principles of functional programming, such as pure functions, recursion, and first-class functions. Although they have different type systems and syntax, they share a common emphasis on function evaluation and state immutability.