# Numpy, Pandas & Matplotlib

## Numpy

### arange

This is like range, expect we can have fractional values. 

```python
np.arange(0.25, 100/6, 3.5)
-> array([ 0.25, 3.75, 7.25, 10.75, 14.25])
```

### linspace

Another function that returns an array, except we can say the range, and the number of numbers that we need. `linspace` will return equally spaced numbers in that range.

```python
np.linspace(1, 20, 3)
-> array([ 1. , 10.5, 20. ])
```

