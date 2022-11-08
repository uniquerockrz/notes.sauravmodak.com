---
sidebar_position: 1
---

# Intro To Deep Learning

Deep Learning is machine learning based on artificial neural networks in which we do multiple layers of processing to extract progressively higher level features of data. It is quite related to Machine Learning, where we convert data into numbers and then find patterns in those numbers. 

![](../../assets/Pasted%20image%2020221001191909.png)

## Machine Learning vs Traditional Programming

![](../../assets/Pasted%20image%2020221001192133.png)

In a traditional programming, we write the rules using code and covert some input to output. In the above example, we have the inputs, the ingredients of the dish, and the recipe, which finally produces the output, the food. 

Machine Learning and deep learning on the other hand, recipe is not provided, we have the input, and the ideal output, and the machine learning or deep learning algorithms figure out the recipe. 

However, remember you don't need to use machine learning/deep learning everywhere. If you can come up with a simple rule based system which you can code up, you can probably use that. 

However, machine learning or deep learning are best suited for the following scenarios:

* If there is a long list of rules which cannot be all tracked. 
* It's good for continually changing environments (because models can be retrained, or they can guess the output of unknown inputs)
* Can be used for discovering insights or work on a large collection of data.

You should however not use deep learning in this following scenarios. 

* When you require explainability, since deep learning models are essentially a black box.
* When you can solve the problem using a simple rule based system. 
* When errors are unacceptable (like in high priority environments such as finance and healthcare).
* When you don't have enough data. 

Machine Learning models typically work best with structured data, such as rows and columns data in a spreadsheet. Deep learning models typically work better in unstructured data, such as text, audio, images etc. 

## What Are Neural Networks 

Before understanding neural networks, we can learn as to how neural networks work.

![](../../assets/Pasted%20image%2020221025210925.png)

As you can see in the image above, neural networks take some input, which can be text, images or audio. We convert that to a numerical representation, called a tensor, and then input that to a neural network. The neural network does its thing, and then outputs another numerical representation. We then have to parse this output to the output that we can understand. 

When we take the neural network itself, it can be broken down to the following.

![](../../assets/Pasted%20image%2020221025211457.png)

There is an input layer, which can have multiple neurons, there is a hidden layer in the middle and at the end there is an output layer, which can output numerical representations or probabilities. 

Note that when we say neural network learns patterns, we mean embeddings, weights, feature representation or feature vectors. 

## Types Of Learning

Like Machine Learning, there can be different types of learning in deep learning. However, they can be classified in the major 4 types. 

* Supervised Learning: You have data and labels for all records, and you train a model on that. 
* Semi Supervised Learning: You have data and labels for some records, and you train on that. Then you find the labels of unlabelled data. 
* Unsupervised Learning: You don't have labels for the data, you just ask the algorithms to find patterns in data. 
* Transfer Learning: You train a neural network, and then use the knowledge gained by it to train another neural network. 

## What Is A Tensor? 

A tensor is just a numerical representation of information. Since deep learning algorithms work with just numbers, we need to convert the data that we are training or predicting to numbers to be useful for neural networks. This is usually a two dimensional array of numbers which can be fractions. 