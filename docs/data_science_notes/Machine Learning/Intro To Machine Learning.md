---
sidebar_position: 1
---

# Into To Machine Learning

**Definition:** A computer is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E.

Example here is Spam Filter:
* E is Training Data (previous emails)
* T is identifying Spam Emails
* P is accuracy, percentage of correctly classified email.

## Types Of ML Systems

There are several ways to categorise ML Systems:

* Supervised vs Unsupervised (Semi Supervised/Reinforcement Learning also falls in this category)
* Online vs Batch Learning
* Instance vs Model Based

### Supervised Learning

In this type of ML systems, you have to give the label as well as the data points, and the ML system learns on them. For example, you give a list of emails and also whether they are spam or not. 

Types of supervised learning:

* Classification: You have definite labels (spam/not spam, cats/dogs).
* Regression: You have continuous labels (stock price).

Some examples of supervised learning are:

* K Nearest Neighbours
* Linear Regression
* Logistic Regression
* Support Vector Machines
* Decision Tress
* Neural Networks

### Unsupervised Learning

In this method, you do not provide labels to data and the algorithm has to figure out and identify patterns from them. 

Some examples of unsupervised learning are:

* Clustering (K Means, DB Scan)
* Anomaly Detection (Credit Card Fraud)
* Visualisation
* Association Rule Learning

There is also something called semi supervised learning, which is a combination of supervised and unsupervised learning. 

### Batch Learning Vs Online Learning

Batch learning requires a lot of computational resources and you train all the data at once. This is required in some algorithms such as K Nearest Neighbours. You can ofcourse retrain the whole model on a regular basis but that again is time and computationally expensive. 

In online learning however, you train or update the system incrementally. It's ideal for time series data and likes. Sometimes the data is too large to fit in memory at once, so that's where online learning is advantageous. 

### Instance Based vs Model Based Learning

In instance based learning, the new instance is matched with currently existing instances based on a similarity measure. 

In model based learning, there exists a boundary between different instances, and the instances are classified accordingly. This can give us new insights. 

## Typical Workflow Of A Machine Learning Problem

1. First plot the data and visualize it.
	1. Usually scatter plots.
	2. Then you can use linear plot. 
	3. You can also use fourier plots. 
	4. t-sne plots. 
2. See if there is a linear relation, if yes, select a linear model.
3. Fit the linear model to the data. 
4. Apply the model on new cases and see the result. 

## Main Challenges Of Machine Learning

The main challenges of machine learning are the following:

### Data Related Challenges

* Insufficient Quantity of Training Data
* Non-representative Training Data
	* Sampling Bias
	* Sampling Noise
* Poor Quality Data
* Irrelevant Features
	* Feature Selection
	* Feature Extraction - mixing several methods. 

### Algorithm Related Challenges

* Overfitting 
* Under-fitting

## Testing & Validation

To test the model, we split the data into training set and test set, and then apply the model on the test set. We find the error rate that way. This error is known as generalisation error. 

Based on this, we can conclude the following:

* Overfitting: Low training error and high test error. 
* Under-fitting: High training error. 

We however, should not choose a model based on the test error. Rather, we should use the test error to interpret which model is better and why. 

A better approach will be to further divide the training set into two, the training set and validation set, and use the validation set to choose the best fitted model.

Even better, it will be better if we have different sources of data, and each of the sources will have a validation data, and we train the model in all the sources of data. 

## Parameters vs Hyper-parameters

Parameters are something that the model learns from the data. 

Hyper-parameters are something that we provide to tune the model. 

## How To Go About Doing A Machine Learning Project

1. Frame the problem and find the business objective.
	1. Which type of algorithm to use, supervised or unsupervised. 
	2. How to measure performance. 
	3. Choose online vs batch learning.
	4. How good the model has to be to be useful in production (say there is already a baseline model).
2. Get the data
	1. Understand each column
	2. Check if they are numerical and categorical variables
	3. Look at the min/max/median etc for numerical columns
	4. Look at count and frequencies of the categorical variables
	5. Look at histograms
3. Split the data into training and test set which is well represented. 
4. Visualize the data to gain insights.
	1. Scatter plots (very good with correlations)
	2. Pie charts, box plots
	3. Star graphs
	4. Histograms
5. Experiment with attribute combinations
	1. Take a log of values
	2. Take an average of values
6. Prepare the data
	1. Handle missing features
	2. Handle the categorical variables
		1. Assign a numerical constant to each category
		2. Use a one hot encoder
		3. Use vector embeddings
	3. Scale features
		1. Shift the values to be between zero and one
		2. Ensure that the mean is zero and standard deviation is one. 
7. Train the model
	1. Use validation data here
	2. Use cross validation techniques to get an idea about the test error
	3. Tune the model using hyper-parameters
		1. Use grid search
		2. Use random search (as sometimes grid search can be time intensive)
8. Fine tune your model
	1. Use ensembling
	2. Use stacking
9. Analyse your model, find where the errors are coming from etc
	1. Evaluate your model in test set
10. Launch the model, maintain and monitor your system

## Measuring Errors

### Mean Absolute Error

It's just the summation of absolute values of error, over all the observations. 

$$
\frac{1}{n}\sum_{i=1}^{n}| h(x_{i}) - y_{i} |
$$

Where $n$ is the number of observations, $h$ is the prediction model, $h(x_{i})$ is the predicted value, $y_{i}$ is the actual value. 

### Root Mean Squared Error

Similar to MAE, but we take a square root here instead of modulus. 

$$
\sqrt[]{\frac{1}{n} \sum_{i=1}^{n} {( h(x_{i}) - y_{i} )}^{2} }
$$

### Accuracy

This is sued for classification problems, where we just divide the number of accurate predictions by the total number of predictions. 

$$
\frac{1}{n} \sum_{i=1}^{n} I \left\{ h(x_i) == y_i \right\}
$$

However, remember that the accuracy can be highly misleading, especially in cases where the datasets are imbalanced, like for example cancer diagnosis, credit card fraud etc. 

### Confusion Matrix

It's a better way to measure classification, and is based on four values. 

![](../../assets/Pasted%20image%2020220923201903.png)

We take two values here:

* **Precision**: How many which we detected positive are actually positive
		Precision = TP / (TP + FP)
* **Recall**: How many of actual positives have we predicted correctly
		Recall = TP (TP + FN)
* F1 score:
		2 * Precision * Recall / Precision + Recall
