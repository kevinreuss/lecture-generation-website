# Bresenham’s Line Algorithm

Bresenham’s Line Algorithm is a method used in computer graphics for drawing straight lines. It uses only integer addition, subtraction, and multiplication by 2, which makes it significantly faster than traditional line algorithms using real numbers and floating point arithmetic.

## Algorithm Overview

The algorithm starts by calculating the difference between the starting and ending points in both dimensions (dx, dy) and determining which axis, x or y, is the "driving axis". The driving axis is the one that has the greatest difference.

Then, it initializes two error variables, `E1` and `E2`, which are used to decide when to increment the non-driving axis. `E1` is set to twice the difference of the non-driving axis, and `E2` is set to `E1` minus twice the difference of the driving axis.

## Algorithm Steps

Here's the pseudocode for the algorithm:

```python
def bresenhamLine(x0, y0, x1, y1):
  dx = abs(x1 - x0)
  dy = abs(y1 - y0)
  sx = 1 if x0 < x1 else -1
  sy = 1 if y0 < y1 else -1
  err = dx - dy

  while True:
    plot(x0, y0)
    if x0 == x1 and y0 == y1:
      break
    e2 = 2 * err
    if e2 > -dy:
      err = err - dy
      x0 = x0 + sx
    if e2 < dx:
      err = err + dx
      y0 = y0 + sy
```

In each loop iteration, the algorithm plots the point (x0, y0), checks if the end of the line has been reached, and if not, it adjusts the error term and increments x0 and/or y0.

## Notes

This algorithm only draws lines, but it can be extended to draw circles, ellipses, and other shapes. The key is to use integer arithmetic for speed and to avoid the rounding errors that can occur with floating point arithmetic.
