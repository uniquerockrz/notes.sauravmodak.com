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