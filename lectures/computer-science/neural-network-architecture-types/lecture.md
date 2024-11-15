# Neural Network Architecture Types

Neural networks can be broadly categorized into four main architecture types: Feedforward Neural Network (FNN), Radial basis function Neural Network (RBFNN), Recurrent Neural Network (RNN), and Convolutional Neural Network (CNN).

## Feedforward Neural Network (FNN)

FNN is the simplest type of artificial neural network. In this architecture, information moves in only one direction—forward—from the input nodes, through the hidden nodes (if any), and to the output nodes. No cycles or loops are present.

For instance, a basic FNN can be implemented using Keras like this:

```python
from keras.models import Sequential
from keras.layers import Dense

model = Sequential()
model.add(Dense(32, activation='relu', input_dim=100))
model.add(Dense(1, activation='sigmoid'))
model.compile(optimizer='rmsprop', loss='binary_crossentropy', metrics=['accuracy'])
```

## Radial basis function Neural Network (RBFNN)

RBFNN is a type of ANN that uses radial basis functions as activation functions. It differs from other neural networks due to its fast learning speed. 

```python
from sklearn.cluster import KMeans
from scipy.spatial import distance

kmeans = KMeans(n_clusters=2, random_state=0).fit(X)
centers = kmeans.cluster_centers_
d_max = max([distance.euclidean(c, centers) for c in centers])
```

## Recurrent Neural Network (RNN)

RNNs are networks with loops in them, allowing information to persist. They are called recurrent because they perform the same task for every element of a sequence, with the output being depended on the previous computations. 

Here's an example of a simple RNN in Keras:

```python
from keras.models import Sequential
from keras.layers import SimpleRNN

model = Sequential()
model.add(SimpleRNN(32, input_shape=(10, 16)))
```

## Convolutional Neural Network (CNN)

CNNs are primarily used for image processing, named after their mathematical operation called convolution. They are pre-trained models with tens of thousands of images on multiple GPUs for days or weeks.

```python
from keras.models import Sequential
from keras.layers import Conv2D

model = Sequential()
model.add(Conv2D(32, (3, 3), activation='relu', input_shape=(64, 64, 3)))
```
Each of these architectures has its use cases and strengths, and understanding them will help you apply the right type to the right problem.