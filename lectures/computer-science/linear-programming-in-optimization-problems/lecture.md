# Linear Programming in Optimization Problems

Linear Programming (LP) is a mathematical method used to determine the best (optimal) solution in optimization problems, where the objective function and constraints are represented by linear relationships.

## Basics of LP

A linear programming problem consists of:

- **Objective Function**: What we are trying to maximize or minimize.
- **Decision Variables**: The inputs we can control.
- **Constraints**: The conditions that limit the means by which we can achieve our objective.

For instance, consider an optimization problem where we want to maximize the profit (objective function) by selling widgets and gadgets (decision variables), given constraints like production capacity and raw material availability.

## Application of LP

Linear programming has wide applications in fields such as operations research, economics, and computer science. For instance, in logistics, LP can help determine the optimal route for delivery to minimize cost or time.

## LP Solving with Python

Python's `scipy.optimize.linprog` method provides a straightforward way to solve LP problems. Below is a simplified version of the widget and gadget problem:

```python
from scipy.optimize import linprog

# Coefficients of the objective function
c = [-3, -5]  # We want to MAXIMIZE profit, so the coefficients are negative

# Inequality constraints matrix
A = [[1, 0], [0, 2], [3, 2]]  # Widget and gadget constraints

# Inequality constraints vector
b = [4, 12, 18]  # Resource constraints

# Solve the problem
res = linprog(c, A_ub=A, b_ub=b, method='simplex')

print('Optimal value:', -res.fun, '\nX:', res.x)
```

In this snippet, `c` represents the coefficients of the objective function (profit per widget and gadget), `A` and `b` represent the constraints. The `linprog` function solves the problem using the Simplex algorithm and returns the optimal profit and the quantity of widgets and gadgets to produce.

## Conclusion

Linear programming is a powerful tool for solving optimization problems with a linear objective function and linear constraints. Python's `scipy.optimize` module provides a convenient way to solve such problems.