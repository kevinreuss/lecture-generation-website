# Introduction to Machine Learning for Embedded Systems

To comprehend Machine Learning (ML) in the context of embedded systems, we need to investigate how these systems can exploit ML algorithms. Let's start with a typical ML pipeline, which includes data collection, pre-processing, training, validation, and deployment.

## Data Collection and Preprocessing
In embedded systems, the data often comes from sensors or signals. For instance, an accelerometer in a wearable device. Data preprocessing involves cleaning and transforming raw data into a machine-understandable format. It may include normalization, handling missing data, and data augmentation.

## Training and Validation
Training an ML model involves feeding the preprocessed data into an algorithm to learn patterns. The algorithm could be supervised, unsupervised, or reinforcement learning. For an embedded system, regression or classification ML algorithms are often used.

For example, in a temperature control system, we might use a regression algorithm to predict the temperature and a classification algorithm to decide whether to turn the heat on or off. The model's performance is validated using a separate dataset.

## Deployment
Once trained, the ML model is deployed into the embedded system. Given the constraints of embedded devices like limited memory and computational power, lightweight models such as decision trees or linear regression are often used. 

Here's a simple linear regression example using Python's scikit-learn library:

```python
from sklearn.linear_model import LinearRegression
X = [[0, 0], [1, 1], [2, 2]] # Training data
y = [0, 1, 2] # Training targets
reg = LinearRegression().fit(X, y)
```
The model can be used to predict the value of new data points:

```python
reg.predict([[3, 3]]) # Output: array([3.])
```
## On-Device Training and Inference
In some advanced applications, on-device training or inference is used, where the model learns directly from the embedded system without needing to communicate with an external server. This is done using libraries like TensorFlow Lite for Microcontrollers.

To wrap up, implementing ML in embedded systems involves careful consideration of the device's capabilities and the complexity of the ML model. It's a balance between achieving acceptable model performance and maintaining the device's operational requirements.