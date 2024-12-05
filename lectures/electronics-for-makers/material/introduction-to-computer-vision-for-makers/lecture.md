# Introduction to Computer Vision for Makers

Computer Vision (CV) is the science of computers and software systems that can recognize and understand images and scenes. CV is the basis for machine learning (ML) applications like object and gesture recognition, autonomous vehicles, and image restoration.

## Key Concepts

In CV, an image is perceived as an array of pixel values. Depending on the image resolution and color scheme, the array can be a 2D (grayscale images) or 3D (color images) array.

```python
# Importing necessary libraries
from PIL import Image
import numpy as np

# Loading an image
img = Image.open('image.jpg')

# Converting the image into numpy array representation
img_array = np.array(img)
```

These numerical values can be manipulated to apply various CV techniques, such as edge detection, color segmentation, feature matching, etc.

## Image Processing in OpenCV

OpenCV (Open Source Computer Vision Library) is one of the most used libraries for CV tasks. Here's a brief example of how to perform edge detection using OpenCV:

```python
# Importing necessary libraries
import cv2
import numpy as np

# Loading an image
img = cv2.imread('image.jpg', cv2.IMREAD_GRAYSCALE)

# Applying Canny edge detection
edges = cv2.Canny(img, threshold1=30, threshold2=100)

# Displaying the edge detected image
cv2.imshow('Edge Detected Image', edges)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## Machine Learning in Computer Vision

ML plays a crucial role in CV, helping computers to understand and label images. Convolutional Neural Networks (CNNs) are frequently used for image classification tasks, due to their efficiency in spatial data processing.

```python
# Importing necessary libraries
from keras.models import Sequential
from keras.layers import Conv2D

# Creating a model
model = Sequential()

# Adding a convolutional layer
model.add(Conv2D(filters=64, kernel_size=2, padding='same', activation='relu', input_shape=(32, 32, 3)))
```

In this code, a basic CNN model is created and a convolutional layer is added. The model takes an input image of 32x32 pixels with 3 color channels (RGB).

Remember, the field of Computer Vision is vast and continually evolving. It's important to keep exploring and practicing with different tools and algorithms.