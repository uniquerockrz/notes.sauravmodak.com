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
