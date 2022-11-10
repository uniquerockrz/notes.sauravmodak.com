# Linear Regression

Linear regression is one of the simplest machine learning methods out there and it can be widely used for testing out a variety of data science problems. Machine learning however, consists of two variables:

* **response variable**: the variable we are trying to predict, usually represented as y
* **predictor variable**: the variable(s) on which we are trying to predict the response variable. 

This shows one of the examples of linear regression. We have the temperature of the day as the variable t, and the number of ice cream sold as n. We are trying to predict the number of ice cream sold based on the temperature. For this, we are using a linear regression model, which just draws a line through the points plotted on a graph. 

![](../../assets/Pasted%20image%2020220906130330.png)

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

![](../../assets/Pasted%20image%2020220907080640.png)

However, if we change the equation to $y=2x+-2$, it will look like this:

![](../../assets/Pasted%20image%2020220907080757.png)

As you can see, the slope as well as the intercepting point has changed. 
* **Standard Deviation**: It's the square root of the variance as described above. 
* **Normal Distribution**: Also known as the bell curve, it is the most common probability distribution that has some handy properties. 
![](../../assets/Pasted%20image%2020220914135737.png)

## Correlation Does Not Imply Causation

There can be two types of data we can end up working with, one is observational data and another is experimental data. Observational data is something we just observe, and have no control over. Say the temperature of the atmosphere. On the other hand, experimental data is data from experiments that we can control. Say you are in the office and you can control the temperature of the air conditioning. 

In an observational settings, since there are a lot of variables that we can't control, it will be best to assume no causation among variables, even if there seem to be a correlation among them. 

## The Formula Of Linear Regression

The formula of linear regression is just like the line equation, with different symbols. 
$$
y = {\beta_{0}} + {\beta_{1}}x
$$
where ${\beta_{0}}$ is the interceptor and ${\beta_{1}}$ is the slope. We are essentially interested to find the values of these two variables by drawing a line that covers all the points in the space. This line is also known as the least squares line. 

## Using Simple Linear Regression With Statsmodels

We will be building a simple linear regression model using python and statsmodels. In the process we will learn how to predict predictor variables using ordinary least squares. 

We will be using Soccer data of the ProjectPro first project for this. We will be using pandas to load the data from the CSV file, draw plots using matplotlib and then predict using statsmodels ordinary least squares. 

As usual, let's load the libraries and the dataset. 

```python
dataset_path = '../datasets/ProjectPro/EPL_Soccer_MLR_LR.csv'

import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
import statsmodels.api as sm
```

We can get some basic info about this data using the `df.info()`. Most importantly, it shows number of null and non null values. 

```python
df = pd.read_csv(dataset_path)
df.info()
```

![](../../assets/Pasted%20image%2020220919133342.png)

As you can see, there are 202 entries in total, but in all columns, we get all 202 values as non-null. 

A good way to get some basic stats of the numerical fields is using the `describe` function. 

```python
df.describe()
```

![](../../assets/Pasted%20image%2020220919133607.png)

You can also use `head()` to see the first few rows. 

```python
df.head(10)
```

![](../../assets/Pasted%20image%2020220919133658.png)

Since we are doing a linear regression, which tries to draw a straight line, it will be advantageous if we can get the column which is most correlated and try least squares on that. We can use the `corr()` function to find correlations among all the numerical columns. 

```python
df.corr() # correlation analysis
```

![](../../assets/Pasted%20image%2020220919133858.png)

We are interested only the scores here. So we find the column most correlated with score, which is Cost. We can now try building a scatter plot between the cost column and the score. 

```python
plt.scatter(df['Cost'], df['Score'])
```

![](../../assets/Pasted%20image%2020220919134053.png)

The points seems to be somewhat straightly correlated. 

Now, to build the model, we put these columns in two variables, `x` and `y`. We also need to do a test and train split so that we can test the model later and find the accuracy. We can use the function from `sklearn` for this. 

```python
x = df['Cost']
y = df['Score']

x_train, x_test, y_train, y_test = train_test_split(x, y, train_size=0.75, test_size=0.25, random_state=42)
```

Statsmodel doesn't automatically create an intercept, so we will have to do it manually. 

```python
x_train_with_intercept = sm.add_constant(x_train)
```

Finally, we fit the model. 

```python
lr = sm.OLS(y_train, x_train_with_intercept).fit()
```

We can get the constant (intercept) and the slope (the predictor variable's coefficient) using the `params`.

```python
lr.params
```

![](../../assets/Pasted%20image%2020220919134646.png)

And we can also get the summary of the model. 

```python
lr.summary()
```

![](../../assets/Pasted%20image%2020220919134726.png)

## Interpreting The Output

As we can see, statsmodels has given us the estimates for the constant as well as the Cost. If we put those into linear regression formula, we get this. 

$$
y = {0.7921} + {0.1834}x
$$
Where 0.7921 is $\beta_{0}$ and 0.1834 is $\beta_{1}$. This means, for every 0.1834 increase in cost, the score increases by 1. 

We can see the range of the cost, for example, here it is between 32 and 200. If we make an estimate in this range, its called interpolation. However, if we make an prediction outside this range, its called extrapolation. Extrapolated predictions may not be that accurate and the thing to do in many cases. 

## Error Term

Since we cannot fit all the points perfectly into the line of linear regression, there's bound to be an error term in the equation. So, the actual equation becomes:

$$
y = \beta_{0} + \beta_{1}x + \varepsilon 
$$

Where $\varepsilon$ is the error term. We may assume that this has a mean of zero and a variance of $\sigma^{2}$. 

## Confounding Variables or Lurking Variables

The best way to understand confounding variables is using an example. Let's say, we have to estimate why crime is going up in a city using some data. We observe that on days the foot traffic is high, the crime rate rises too. 

However, it may be possible that there are some other variables that are influencing both the foot traffic and the crime. 

![](../../assets/Pasted%20image%2020221109095127.png)

In this example, it maybe the temperature that is influencing both. Such variables are called confounding variables. We should be careful when using confounding variables as estimates to linear regression. 

## How Are The Estimators Calculated?

Remember that the formula of simple linear regression is like this:

$$
y = \beta_{0} + \beta_{1}x
$$

The Q-criterion here is to minimise the sum of square errors. Let's take the points on which we are estimating to be something like this:

![](../../assets/Pasted%20image%2020221110124702.png)

We can fit a line to the above, however, the best line should be pretty close to points. 

![](../../assets/Pasted%20image%2020221110124844.png)

We can take the difference of the points from the line to determine if the line is a good fit. However, some of the differences will be positive and some of the differences will be negative. So it's likely that the values will cancel each other out. 

Instead of taking the difference directly, we can square it, so it will always be positive. This is precisely what's called sum of square errors. 

So, we are trying to minimise the square of the residuals. 

So, the Q-criterion, which we are trying to minimise, is:

$$
\sum_{i=1}^{N} \left [ y_{i} - \left ( \beta_{0} + \beta_{i}.x_{i} \right ) \right ] ^ 2
$$
Which is the `actual value - predicted value` of `i`.

So how do we solve the above? There can be two methods for this:

1. We use a computational method to find the values of $\beta_{0}$ and $\beta_{1}$.
2. We take the partial derivate of Q with respective to $\beta_{0}$ and $\beta_{1}$.

So, the partial derivatives are:

$$
\frac{\partial Q }{\partial \beta_{0}} = -2 \sum_{i=0}^{N} (y_{i} - \beta_{0} - \beta_{i}.x_{i} )
$$

and 

$$
\frac{\partial Q }{\partial \beta_{1}} = -2 \sum_{i=0}^{N} x_{i} (y_{i} - \beta_{0} - \beta_{i}.x_{i} )
$$

And the estimates come out to be:

$$
\beta_{0} = \bar{y} - b_{i}.\bar{x} 
$$

$$
\beta_{1} = \frac{\sum (x_{i}- \bar{x})(y_{i} - \bar{y})}{\sum (x_{i} - \bar{x}) ^ 2}
$$


Where $\bar{x}$ and $\bar{y}$ are means of values of x and y. 

## Properties Of Estimators

Some of the properties of these estimators are:

1. The estimators are unbiased. 
2. They also have minimum variance amongst unbiased linear estimators.