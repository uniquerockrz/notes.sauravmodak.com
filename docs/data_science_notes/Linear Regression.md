# Linear Regression

Linear regression is one of the simplest machine learning methods out there and it can be widely used for testing out a variety of data science problems. Machine learning however, consists of two variables:

* **response variable**: the variable we are trying to predict, usually represented as y
* **predictor variable**: the variable(s) on which we are trying to predict the response variable. 

This shows one of the examples of linear regression. We have the temperature of the day as the variable t, and the number of ice cream sold as n. We are trying to predict the number of ice cream sold based on the temperature. For this, we are using a linear regression model, which just draws a line through the points plotted on a graph. 

![](../assets/Pasted%20image%2020220906130330.png)

If we are using only one variable to predict the outcome, it is known as **simple linear regression**. If we have have multiple predictor variables, we call it **multiple linear regression**. We have to understand the simple linear regression first, before moving into multiple linear regression. 

Some examples where we can use linear regression:

* predicting a car's fuel economy from it's size
* predicting someone's life expectancy from their BMI

## Some Mathematical Concepts

* **Mean**: Mean is just the sum of the numbers in a sequence, divided by the number of numbers.
$$
\frac{\sum_{1}^{n}x_{i}}{n}
$$
Example, the mean of three numbers, 1, 2, 3 is 2. 
* **Variance**: This is another measure that is used to determine the spread of a range of numbers. If the numbers are quite spread out, then the variance will be high. This is calculated by this formula:
$$
\frac{\sum_{1}^{n} (x_{i} - \bar{x})^2 }{n-1}
$$
where $\bar{x}$ is the mean of the sequence.
* **Formula of a line**: We know that the formula of a line is $y=mx+c$. Here, the $m$ is known as the slope, which as you can guess, determines the slope of the line. And $c$ is known as the interceptor, which determines where the line will meet the y axis. As an example, if the equation is $y=x+0$, the line will look like this:

![](../assets/Pasted%20image%2020220907080640.png)

However, if we change the equation to $y=2x+-2$, it will look like this:

![](../assets/Pasted%20image%2020220907080757.png)

As you can see, the slope as well as the intercepting point has changed. 
* **Standard Deviation**: It's the square root of the variance as described above. 
* **Normal Distribution**: Also known as the bell curve, it is the most common probability distribution that has some handy properties. 
![](../assets/Pasted%20image%2020220914135737.png)

## Correlation Does Not Imply Causation

There can be two types of data we can end up working with, one is observational data and another is experimental data. Observational data is something we just observe, and have no control over. Say the temperature of the atmosphere. On the other hand, experimental data is data from experiments that we can control. Say you are in the office and you can control the temperature of the air conditioning. 

In an observational settings, since there are a lot of variables that we can't control, it will be best to assume no causation among variables, even if there seem to be a correlation among them. 
