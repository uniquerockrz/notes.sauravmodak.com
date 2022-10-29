# Tensorflow Basics

Tensorflow is a python framework that can be used to build end to end deep learning models. It has all the tools that we need to build models. However, before we master that, we need to learn  about Tensorflow basics.

## Declaring Variable & Constants

### Constants

Zero dimensional constants in Tensorflow are called scalars. They have magnitude but no dimensions. 

```python
# Create a constant tensor
scalar = tf.constant(7)
scalar
# <tf.Tensor: shape=(), dtype=int32, numpy=7>

# number of dimensions
scalar.ndim
# 0
```

We use the `ndim` function to find the number of dimensions of a tensor. 

Likewise, a 1 dimensional tensor with magnitude and direction is called a vector. A 2 dimensional tensor is called a matrix, and a n-dimensional tensor is called a tensor. 

```python
# create a vector
vector = tf.constant([10, 10])
vector
# <tf.Tensor: shape=(2,), dtype=int32, numpy=array([10, 10], dtype=int32)>

vector.ndim
# 1
```

```python
# create a matrix
matrix = tf.constant([
    [10, 7],
    [19, 91]
])
matrix
'''
<tf.Tensor: shape=(2, 2), dtype=int32, numpy=
array([[10,  7],
       [19, 91]], dtype=int32)>
'''

matrix.ndim
# 2
```

We can also specify the data type using the `dtype` parameter.

```python
# create matrix with different data type
another_matrix = tf.constant([
    [10., 7.],
    [4., 7.],
    [1., 2.]
], dtype = tf.float16)
another_matrix
'''
<tf.Tensor: shape=(3, 2), dtype=float16, numpy=
array([[10.,  7.],
       [ 4.,  7.],
       [ 1.,  2.]], dtype=float16)>
'''
```

By default, Tensorflow chooses 32 bit float for floating point types. However, we can specify `float32` to save space. 

Finally, we can create a 3 dimensional tensor. 

```python
# create a tensor
tensor = tf.constant([
    [
        [1, 2, 3],
        [4, 5, 6]
    ],
    [
        [7, 8, 9],
        [10, 11, 12]
    ],
    [
        [13, 14, 15],
        [16, 17, 18]
    ]
])
tensor
'''
<tf.Tensor: shape=(3, 2, 3), dtype=int32, numpy=
array([[[ 1,  2,  3],
        [ 4,  5,  6]],

       [[ 7,  8,  9],
        [10, 11, 12]],

       [[13, 14, 15],
        [16, 17, 18]]], dtype=int32)>
'''
tensor.ndim
# 3
```

### Variables

Likewise, we can use the `tf.Variable` function to create variables. 

```python
# create a variable and constant tensor
changeable_variable = tf.Variable([10, 7])
unchangeable_variable = tf.constant([10, 7])

changeable_variable, unchangeable_variable
'''
(<tf.Variable 'Variable:0' shape=(2,) dtype=int32, numpy=array([10,  7], dtype=int32)>,
 <tf.Tensor: shape=(2,), dtype=int32, numpy=array([10,  7], dtype=int32)>)
'''
```

We can use the assign function to change values in a variable. However, this function will not work in case of constants. 

```python
# change an element in variable tensor
changeable_variable[0].assign(7)
changeable_variable

# <tf.Variable 'Variable:0' shape=(2,) dtype=int32, numpy=array([7, 7], dtype=int32)>
```

Note, we will not be generating tensors by hand most of the time. Tensorflow already has functions to do it for us, by reading the raw data. 

### Random Tensors

Random tensors are useful because tensorflow uses random tensors to initialise the weights when building a neural network. Then it changes the numbers as it discovers patterns and finally arrives at the final weight. 

We can create random tensors from uniform and normal distributions like this.

```python
tf.random.uniform(shape=(3, 3), seed=42)
'''
<tf.Tensor: shape=(3, 3), dtype=float32, numpy=
array([[0.95227146, 0.67740774, 0.79531825],
       [0.75578177, 0.4759556 , 0.6310148 ],
       [0.18602037, 0.11430776, 0.3362218 ]], dtype=float32)>
'''
```

```python
tf.random.normal(shape=(3, 3), seed=42)
'''
<tf.Tensor: shape=(3, 3), dtype=float32, numpy=
array([[-0.28077507, -0.1377521 , -0.6763296 ],
       [ 0.02458041, -0.89358455, -0.82847327],
       [ 1.2068944 ,  1.3810157 , -1.4557977 ]], dtype=float32)>
```

Giving the same seed with generate the same tensors every time.  

### Shuffling Tensors

We can shuffle tensors using the `shuffle` function. 

```python
unshuffled_tensor = tf.constant([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])
unshuffled_tensor

'''
<tf.Tensor: shape=(3, 3), dtype=int32, numpy=
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]], dtype=int32)>
'''

tf.random.shuffle(unshuffled_tensor, seed=12)

'''
<tf.Tensor: shape=(3, 3), dtype=int32, numpy=
array([[4, 5, 6],
       [7, 8, 9],
       [1, 2, 3]], dtype=int32)>
'''
```

Shuffle is useful in the case say we have an organised set of images which are in a non-random order and we need to shuffle the files to get a random representation so that we get a good training set. 

### Seeds in Tensorflow

There are two types of seeds in Tensorflow, a global seed and an operational seed. Both are used in conjunction to generate random numbers, if they are set. 

```python
# setting a global seed
tf.random.set_seed(13)

# generates different numbers everytime
tf.random.uniform([1]), tf.random.uniform([1])
'''
(<tf.Tensor: shape=(1,), dtype=float32, numpy=array([0.25227463], dtype=float32)>,
 <tf.Tensor: shape=(1,), dtype=float32, numpy=array([0.50676847], dtype=float32)>)
'''
```

### Ones, Zeros and Using Numpy Arrays In Tensors

Like numpy, tensorflow has functions for generating zeros and ones. You can also directly convert numpy arrays into tensors and use advantage of GPU calculation. 

```python
tf.ones(shape=(4,4))
'''
<tf.Tensor: shape=(4, 4), dtype=float32, numpy=
array([[1., 1., 1., 1.],
       [1., 1., 1., 1.],
       [1., 1., 1., 1.],
       [1., 1., 1., 1.]], dtype=float32)>
'''

tf.zeros(shape=(4,4))
'''
<tf.Tensor: shape=(4, 4), dtype=float32, numpy=
array([[0., 0., 0., 0.],
       [0., 0., 0., 0.],
       [0., 0., 0., 0.],
       [0., 0., 0., 0.]], dtype=float32)>
'''

import numpy as np
numpy_arr = np.arange(1, 25)
tf.constant(numpy_arr, shape=(4, 3, 2))

'''
<tf.Tensor: shape=(4, 3, 2), dtype=int64, numpy=
array([[[ 1,  2],
        [ 3,  4],
        [ 5,  6]],

       [[ 7,  8],
        [ 9, 10],
        [11, 12]],

       [[13, 14],
        [15, 16],
        [17, 18]],

       [[19, 20],
        [21, 22],
        [23, 24]]])>
'''
```

In the last step, if you give a custom shape, you will have to make sure that the number of elements in the numpy array adds up to the number of elements in custom shape. 

## Getting Information From Tensors

### Getting Dimensions, Data Type, Shape & Size

You can get information from tensors using attributes and other functions

```python
rank_4_tensor.dtype # data types
# tf.float32

rank_4_tensor.ndim # dimensions
# 4

tf.shape(rank_4_tensor) # shape
# <tf.Tensor: shape=(4,), dtype=int32, numpy=array([4, 4, 4, 4], dtype=int32)>

tf.size(rank_4_tensor) # size
# <tf.Tensor: shape=(), dtype=int32, numpy=256>
```

### Indexing Tensors

You can index tensors like you index arrays. 

```python
rank_3_tensor_elements = np.arange(0, 27)
rank_3_tensor = tf.constant(rank_3_tensor_elements, shape=(3, 3, 3))
rank_3_tensor
'''
<tf.Tensor: shape=(3, 3, 3), dtype=int64, numpy=
array([[[ 0,  1,  2],
        [ 3,  4,  5],
        [ 6,  7,  8]],

       [[ 9, 10, 11],
        [12, 13, 14],
        [15, 16, 17]],

       [[18, 19, 20],
        [21, 22, 23],
        [24, 25, 26]]])>
'''
rank_3_tensor[1, 1, 1] # get a specific element
# <tf.Tensor: shape=(), dtype=int64, numpy=13>

rank_3_tensor[-1, :, :]
'''
<tf.Tensor: shape=(3, 3), dtype=int64, numpy=
array([[18, 19, 20],
       [21, 22, 23],
       [24, 25, 26]])>
'''
```

You can also get ranges of elements from tensors, like you do in a python list. 

## Operations On Tensors

### Adding Dimensions To Tensors

You can add dimensions or expand tensors in two ways.

```python
rank_3_tensor[..., tf.newaxis]
tf.expand_dims(rank_3_tensor, -1)
```

With the expand dims, you can specify the axis you need to expand the dimension on. 

### Reshaping Tensors

You can reshape tensors, provided they have the same number of elements in them.

```python
tensor_ones = tf.ones(shape=(5, 2))
tensor_ones

'''
<tf.Tensor: shape=(5, 2), dtype=float32, numpy=
array([[1., 1.],
       [1., 1.],
       [1., 1.],
       [1., 1.],
       [1., 1.]], dtype=float32)>
'''

tf.reshape(tensor_ones, shape=(2, 5))
'''
<tf.Tensor: shape=(2, 5), dtype=float32, numpy=
array([[1., 1., 1., 1., 1.],
       [1., 1., 1., 1., 1.]], dtype=float32)>
'''
```

### Transposing Tensors

We can transpose tensors, which is just changing the axis of tensors, rather than reshaping

```python
tensor_ex0 = tf.constant([[1, 2], [3, 4], [5,6]])
tensor_ex0
'''
<tf.Tensor: shape=(3, 2), dtype=int32, numpy=
array([[1, 2],
       [3, 4],
       [5, 6]], dtype=int32)>
'''
tf.transpose(tensor_ex0)
'''
<tf.Tensor: shape=(2, 3), dtype=int32, numpy=
array([[1, 3, 5],
       [2, 4, 6]], dtype=int32)>
'''
```

### Arithmetic Operations On Tensors

You can do simple math operations on tensors with arithmetic operators. 

```python
tensor_ex1 = tf.constant([[1, 2], [3, 4]])
tensor_ex1 + 10
'''
<tf.Tensor: shape=(2, 2), dtype=int32, numpy=
array([[11, 12],
       [13, 14]], dtype=int32)>
'''
tf.add(tensor_ex1, 10)
'''
<tf.Tensor: shape=(2, 2), dtype=int32, numpy=
array([[11, 12],
       [13, 14]], dtype=int32)>
'''
```

You can also use built in functions for these operations, which can give you the advantages of GPU acceleration. Like add, other operations such as subtract, multiply and divide are also supported. 

### Matrix Multiplication Of Tensors

We can matrix multiply two tensors using the `matmul` function.

```python
tensor_ex2 = tf.random.normal(shape=(2, 2))
tensor_ex3 = tf.random.normal(shape=(2, 2))

tensor_ex2, tensor_ex3
'''
(<tf.Tensor: shape=(2, 2), dtype=float32, numpy=
 array([[-0.9487271 ,  1.3044667 ],
        [-1.1531727 , -0.28560743]], dtype=float32)>,
 <tf.Tensor: shape=(2, 2), dtype=float32, numpy=
 array([[-0.1856016, -1.1418061],
        [ 0.0194767, -2.7855177]], dtype=float32)>)
'''

tf.matmul(tensor_ex2, tensor_ex3)
'''
<tf.Tensor: shape=(2, 2), dtype=float32, numpy=
array([[ 0.20149197, -2.550353  ],
       [ 0.20846802,  2.1122642 ]], dtype=float32)>
'''
```

Remember, the number of columns of the first matrix need to be equal to the number of rows of the second matrix. If it is not, you should transpose the matrix so that they can be multiplied. 

### Changing Data Type Of Tensors

You can change the data type of tensors using the cast method. Sometimes, 16 bit precision tenors work faster than 32 bit precision. 

```python
tensor_ex3 = tf.random.normal(shape=(2, 2))
tensor_ex3
'''
<tf.Tensor: shape=(2, 2), dtype=float32, numpy=
array([[-1.4116935 ,  0.1200662 ],
       [-0.72520065, -1.0911381 ]], dtype=float32)>
'''

tf.cast(tensor_ex3, tf.float16)
'''
<tf.Tensor: shape=(2, 2), dtype=float16, numpy=
array([[-1.412  ,  0.12006],
       [-0.725  , -1.091  ]], dtype=float16)>
'''
```

## Aggregation Of Tensors

### Getting Absolute, Minimum, Maximum, Mean, Sum, Variance and Standard Deviation Of A Tensor

You can get these values with the help of handy functions

```python
tensor_ex4 = tf.random.normal(shape=(3, 3))
tensor_ex4
'''
<tf.Tensor: shape=(3, 3), dtype=float32, numpy=
array([[-0.5971814 , -0.99537617,  1.035538  ],
       [ 0.02057712, -0.12836641, -0.9310614 ],
       [-1.7767631 , -1.466424  ,  0.08939307]], dtype=float32)>
'''

tf.abs(tensor_ex4) # absolute values
'''
<tf.Tensor: shape=(3, 3), dtype=float32, numpy=
array([[0.5971814 , 0.99537617, 1.035538  ],
       [0.02057712, 0.12836641, 0.9310614 ],
       [1.7767631 , 1.466424  , 0.08939307]], dtype=float32)>
'''

tf.reduce_min(tensor_ex4) # minimum
# <tf.Tensor: shape=(), dtype=float32, numpy=-1.7767631>

tf.reduce_max(tensor_ex4) # maximum
# <tf.Tensor: shape=(), dtype=float32, numpy=1.035538>

tf.reduce_mean(tensor_ex4) # mean
# <tf.Tensor: shape=(), dtype=float32, numpy=-0.5277405>

tf.reduce_sum(tensor_ex4) # sum
# <tf.Tensor: shape=(), dtype=float32, numpy=-4.7496643>

tf.math.reduce_variance(tensor_ex4) # variance
# <tf.Tensor: shape=(), dtype=float32, numpy=0.67913365>

tf.math.reduce_std(tensor_ex4) # standard deviation
# <tf.Tensor: shape=(), dtype=float32, numpy=0.82409567>
```


