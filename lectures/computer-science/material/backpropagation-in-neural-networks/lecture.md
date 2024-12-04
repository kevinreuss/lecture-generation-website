# Backpropagation in Neural Networks

Backpropagation is a widely used algorithm in training feedforward neural networks for supervised learning tasks. It’s a method used to adjust the weights of the neural network based on the error rate obtained in the previous epoch (actual output vs desired output).

## High-Level Overview

Backpropagation works by using a loss function to calculate how far the network's output is from the desired output. This error is then propagated back through the network, one layer at a time, and the weights are updated according to the amount they contributed to the error. This is done using the chain rule of differentiation, which is essential to calculate the gradient of the loss function with respect to the weights.

## The Math Behind Backpropagation

Let's say we have a simple network with a single hidden layer and an output layer, both using the sigmoid activation function. The loss function is mean squared error (MSE).

The MSE loss function is defined as:

```python
def mse(y_true, y_pred):
  return np.mean(np.square(y_true - y_pred))
```

The derivative of the MSE function is:

```python
def mse_derivative(y_true, y_pred):
  return 2 * (y_pred - y_true) / y_true.size
```

The sigmoid activation function and its derivative are:

```python
def sigmoid(x):
  return 1 / (1 + np.exp(-x))

def sigmoid_derivative(x):
  return sigmoid(x) * (1 - sigmoid(x))
```

Using these, the gradients of the loss with respect to the weights can be calculated and the weights can then be updated.

## In Practice

In practice, we use libraries such as TensorFlow or PyTorch that handle backpropagation automatically. However, understanding the underlying principles allows us to better understand what these libraries are doing under the hood, and can be invaluable when debugging or when trying to improve the performance of our networks.