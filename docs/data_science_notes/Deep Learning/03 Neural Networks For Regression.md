# Neural Networks For Regression

One of the simplest use case of regression problems for Neural Networks is to predict the dependent variable from a set of independent variable. The classic example is to predict the price of a house from its different features. 

Another example of a regression problem is to find the boundaries of an object from an image. This is useful in cases like image detection. 

## Inputs And Outputs To A Regression Problem

Since we cannot directly give the features to the neural network, we need to encode it some way. One of the ways is to convert that to a tensor and feed that as the input to the neural network. 

The example here shows how we can use one hot encoding to encode three features, the number of bedrooms, the number of garages and the number of bathrooms. 

![](../../assets/Pasted%20image%2020221108143331.png)

We take this tensor and feed it to a deep learning algorithm. This algorithm learns from a bunch of other data like this, as we are using supervised learning, and then gives us a predicted output. 

Inputs and outputs and there shapes are one of the most crucial elements to learn about deep learning. 

## Anatomy Of A Neural Network 

As we have seen earlier, the anatomy of a neural network looks somewhat like this:

![](../../assets/Pasted%20image%2020221108144042.png)

These are some of the major parts of a neural network:

![](../../assets/Pasted%20image%2020221108145801.png)

### Input Layer

The number of neurons here depend on the shape of the input, or the features. So, if we have three features (the number of bedrooms, bathrooms and garages), the number of neurons here will be 3. 

### Hidden Layers 

This depends on the type of problem. Typically, you should have at-least 1 hidden layer, and you can have upto unlimited hidden layers.

#### Number of Neurons Per Hidden Layer

This is also problem specific. But typically, you can have from 10 to 100 neurons per hidden layer. 

### Output Layer

The shape of the output layer depends on the type of the problem, but for a regression problem, it is typically 1. 

### Hidden Activation Function

Usually this is ReLU (rectified linear unit)

### Output Activation Function

It can be None, ReLU or Logistic/Tanh

### Loss Function

This can be MSE (mean squared error) or MAE (mean absolute error) or Huber (combination of MSE and MAE, useful in case of outliers). This loss function measures how wrong our predictions are. 

### Optimiser

This can be SGD (Stochastic Gradient Descent) or Adam. The optimiser works with the neural network to determine how to reduce the loss function. 

### The Code

This is how it looks in the code. There are three steps of building a neural network. The first, we have to define the model. The second, we have to compile the model and here we provide the optimiser and the loss function. And at the end, we provide the data to train the model.

![](../../assets/Pasted%20image%2020221108150019.png)

## An Example

We know that we have to take these following steps to make a model.

![](../../assets/Pasted%20image%2020221108213327.png)

We will follow these steps one by one to create our first neural network.

### The Data

We can define the data as numpy arrays as follows:

```python
# create the features
X = np.array([-7.0, -4.0, -1.0, 2.0, 5.0, 8.0, 11.0, 14.0])


# create the labels
y = np.array([3.0, 6.0, 9.0, 12.0, 15.0, 18.0, 21.0, 24.0])
```

If we plot this, we will be able to see there is a linear relationship between `X` and `y`.

```python
# visualize
plt.scatter(X, y)
```

![](../../assets/Pasted%20image%2020221108213536.png)

We can convert these data into tensors to proceed. 

```python
# Turn numpy arrays into tensors
X = tf.constant(X),
y = tf.constant(y),

X, y
'''
((<tf.Tensor: shape=(8,), dtype=float64, numpy=array([-7., -4., -1.,  2.,  5.,  8., 11., 14.])>,),
 (<tf.Tensor: shape=(8,), dtype=float64, numpy=array([ 3.,  6.,  9., 12., 15., 18., 21., 24.])>,))
'''
```

We set a random seed so that our work is reproducible. 

```python
tf.random.set_seed(42)
```

Then we define the model using Sequential API. 

```python
# Create the model using Sequential API

model = tf.keras.Sequential([
    tf.keras.layers.Dense(1)
])
```

There is also another way that we can create the model. 

```python
# another way of creating the model
model2 = tf.keras.Sequential()
model2.add(tf.keras.layers.Dense(1))
```

We compile the model. Here we are taking the mean absolute error as loss, and stochastic gradient descent as the optimiser. We also want to display some metrics, that is mean absolute error. 

```python
model.compile(loss=tf.keras.losses.mae, optimizer=tf.keras.optimizers.SGD(), metrics=['mae'])
```

Finally we fit the model with our `X` and `y` values. Since these arrays are single dimensions, we need to expand their dimensions so that they can be fitted well. We also run this only for 5 epochs. 

```python
model.fit(tf.expand_dims(X, axis=-1), tf.expand_dims(y, axis=-1), epochs=5)
```

We will see some output like these. It will also display the metrics that we provided, the mean absolute error. 

![](../../assets/Pasted%20image%2020221108214350.png)

As we can see there is an error in prediction upto 10.31. 

We can then use the predict function to predict a value. 

```python
model.predict([[17.0]])
# array([[[15.741023]]], dtype=float32)
```

This gives an output of 15.74, which is quite off from the actual value 27. 

