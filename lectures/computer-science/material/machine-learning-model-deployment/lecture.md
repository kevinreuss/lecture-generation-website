# Machine Learning Model Deployment

Machine Learning Model Deployment is the process of making your model available in a production environment, where it can provide predictions to other software systems. It is one of the last stages of the machine learning pipeline.

Let's consider an example of deploying a machine learning model using Flask, a popular Python-based micro web framework. 

Assume we have trained a simple linear regression model for predicting house prices:

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
```

We now want to deploy this model so that it can be used by others. Here's how we could do that with Flask:

```python
from flask import Flask, request, jsonify
import pickle

# Load the model
model = pickle.load(open('model.pkl','rb'))

app = Flask(__name__)

@app.route('/api',methods=['POST'])
def predict():
    # Get data from POST request
    data = request.get_json(force=True)

    # Make prediction using model loaded from disk as per the data
    prediction = model.predict([[np.array(data['exp'])]])

    # Take the first value of prediction
    output = prediction[0]

    return jsonify(output)

if __name__ == '__main__':
    app.run(port=5000, debug=True)
```

In this example, we use Flask to create a web server that accepts POST requests at the `/api` endpoint. When a POST request is received, it takes the data from the request, uses it to make a prediction with our model, and then returns that prediction in the response.

Once we have this setup, the model can be called from any application that can send HTTP requests. 

On the client side, here's an example of how we might use Python's `requests` library to send data to the model and receive a prediction:

```python
import requests
import json

url = 'http://localhost:5000/api'
data = {'exp': 1.8}
response = requests.post(url, json=data)

print(response.json())
```

This is a very basic example, but the principles remain the same for more complex models and applications: once you have a trained model, you wrap it in a server, write an endpoint that can accept data, use that data to make a prediction with the model, and return the prediction in the response.