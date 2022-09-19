# Numpy

Numpy arrays are different from python arrays in the sense that they are of the same data type, and have the same dimensions. If they don't have the same data types and dimensions, numpy will throw and error. 

You can convert a python array to numpy using:

```python
array = np.array([[1, 2, 3], [4, 5, 6]])
```

## arange

This is like range, expect we can have fractional values. 

```python
np.arange(0.25, 100/6, 3.5)
-> array([ 0.25, 3.75, 7.25, 10.75, 14.25])
```

## linspace

Another function that returns an array, except we can say the range, and the number of numbers that we need. `linspace` will return equally spaced numbers in that range.

```python
np.linspace(1, 20, 3)
-> array([ 1. , 10.5, 20. ])
```

## Dot Products

Let's say, we have two arrays, one with prices and one with items.

```python
prices = np.array([[3, 7, 12, 18, 6], [3.6, 8.4, 14.4, 21.6, 7.2]])

items = np.array([
    [0, 3, 6, 1, 0],
    [1, 6, 2, 0, 0],
    [23, 6, 8, 3, 5],
    [5, 7, 2, 9, 4],
    [3, 4, 1, 8, 7]
])
```

We can multiply them to get the final prices. Depending on dimensions, we have to transpose the matrix if needed.

```python
items.dot(prices.T)

-> array([[111. , 133.2], [ 69. , 82.8], [291. , 349.2], [274. , 328.8], [235. , 282. ]])
```

Remember, in order to do dot products:

* Number of columns in first matrix should be equal to number of rows in the second matrix. In the example above, when we take the transpose of `prices (2x5)`, we get `prices (5x2)`. So here the columns are 2, and rows are 5. The number of columns in `items (5x5)` is 5, which is equal to number of rows in `prices`.
* The resultant matrix will have number of rows of the first matrix (5 here) and number of columns of second matrix (2 here)

## Inverses

Inverse of a matrix is simply the reciprocal of a matrix. So we take each item of a matrix and divide it by 1. 

Inverse of a matrix, when multiplied by the original matrix, will give us an identity matrix. 

So, in the above example, the inverse of matrix `items` is:

```python
np.linalg.inv(items)

-> 
array([[-0.05275779, -0.0263789 , 0.04316547, 0.0383693 , -0.05275779], [-0.05372625, 0.19429072, -0.01023796, 0.00585685, 0.00396606], [ 0.18755765, -0.06968272, 0.00913116, -0.03675521, 0.01448072], [ 0.03583287, -0.16477587, -0.02407305, 0.20296071, -0.09878251], [-0.01443461, 0.09855193, 0.01355838, -0.24649511, 0.27402693]])
```

We can use this inverse to get the prices of the items, by dot product of the total amounts. 

```python
np.linalg.inv(items).dot(amounts)

-> 
array([[ 3. , 3.6], [ 7. , 8.4], [12. , 14.4], [18. , 21.6], [ 6. , 7.2]])
```


