# Classification Using Perception And Adaptive Neurons

When we were trying to determine as how the human brain works, scientists proposed a theory. They proposed that the nerve cells within our brain is a binary gate, on which several inputs can be applied. Only when the cell input exceeds a certain threshold, then the neurons fire an output. 

This was further enhanced by theory of perception later. An algorithm was proposed, which showed that the neurons can automatically learn the weight coefficients that can be then multiplied with the input features in order to make the decision whether the neuron will fire or not. 

## What Is An Artificial Neuron

We can think of artificial neurons in the context of binary classification. We can think that artificial neurons take an input of `x`, say $[x_{1}, x_{2}, x_{3} \dots x_{n}]$ and multiply that by the weights say $[w_{1}, w_{2}, w_{3} \dots w_{n}]$. When we do this we get `z` = $w_{1}.x_{1} + w_{2}.x_{2} + \dots + w_{n}.x_{n}$. The process of finding these `w` or weights is called training. 

If the final value of `z` is greater that a threshold, say $\Theta$, we assign the class `1` to it, else we assign `0`. 

We can simplify this equation further. We can take a value of `b` which is equal to $-\Theta$, the negative value of the threshold. Then we can add that directly to the equation. 

$z = w_{1}.x_{1} + w_{2}.x_{2} + \dots + w_{n}.x_{n} + b$

So, we can now say that the target class will be 0 if `z` is less than zero, and 1 if `z` is greater than zero. 

Thus, `z` can be visualised as follows:

![](../../assets/Pasted%20image%2020221115094708.png)

## How Does The Perceptron Update Weights

The number of weights of the perceptron depends on the number of features, based on which we are trying to predict the target variable. However, since we are trying to visualize the results, we will keep ourselves limited to two feature variables. 

Initially, the weights are assigned to zero or very small random values. We then use the above equation to determine whether the target is correctly classified or not. If the target is correctly classified, the values of the weights and biases remain unchanged. Else, we change the weights according to this equations. 

$$
\Delta w_{j} = lr * (y_{i} - \hat{y}_{i}).x_{i}
$$
$$
\Delta b = lr * (y_{i} - \hat{y}_{i})
$$

As you can see, both the equations depend on a `lr` variable, which is the learning rate, a small value between zero and one. 

One must note that for the perceptron algorithm to converge, the classes must be linearly separable. 


![](../../assets/Pasted%20image%2020221117135945.png)

We can summarize the perceptron algorithm as follows:

![](../../assets/Pasted%20image%2020221117140033.png)

## Coding A Perceptron In Python

The code of the perceptron class is as follows:

```python
# The Perceptron class
class Perceptron:
    def __init__(self, learning_rate=0.01, epochs=50, random_state=42) -> None:
        self.learning_rate = learning_rate
        self.epochs = epochs
        self.random_state = random_state

    def fit(self, X, y):
        random_generator = np.random.RandomState(self.random_state)
        self.w_ = random_generator.normal(loc=0.0, scale=0.01, size=X.shape[1])
        # self.w_ = np.zeros(X.shape[1])

        self.b_ = np.float_(0.)
        self.errors_ = []

        for i in range(self.epochs):
            n_errors = 0
            for xi, target in zip(X, y):
                update = self.learning_rate * (target - self.predict(xi))
                self.w_ += update * xi
                self.b_ += update

                if update != 0.0:
                    n_errors += 1

            print('Epoch: {}, Errors: {}, Weights: {}, Bias: {}'.format(i, n_errors, self.w_, self.b_))
            self.errors_.append(n_errors)
        
        return self
    
    def net_input(self, X):
        return np.dot(X, self.w_) + self.b_
    
    def predict(self, X):
        return np.where(self.net_input(X) >= 0.0, 1, 0)
```

The class takes three parameters, the learning rate, number of epochs, or the number of iterations to go over the dataset, and the random state. 

We call the `fit()` method to go over the dataset in set number of epochs and find the ideal weights. Once that's done, we can use the `predict()` method to find the new classes of data. 

## Classification Of IRIS Data Using Perceptron

We can load the IRIS data and classify using Perceptron using two features, sepal length and petal length, and into two classes, Setosa and Versicolor. If we plot them as a scatter plot, we get this, which shows the classes are linearly separable. 

![](../../assets/Pasted%20image%2020221117142012.png)

On running the perceptron algorithm and fitting the weights, we get the following decision boundary.

![](../../assets/Pasted%20image%2020221117142111.png)

You can see the accompanying code in the notebook. 

## Classifying More Than Two Classes

We can use binary classification for classifying more than one classes. We can use a method called one versus all. In this method, the target class is taken as one class, and all other classes is taken as the second binary class. 

We need to create multiple models to cover this classification case, as for each target class we will have to create a separate model. 