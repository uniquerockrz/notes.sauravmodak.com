# SFrame

SFrame is a dataframe library which can be used to load large amounts of data. The biggest difference with python is that it can load and work on huge amounts of data as the whole data is not loaded into memory, but a part of it can also be written to disk. 

## Loading SFrame & Data

You can install the `turicreate` library to use SFrame. 

```python
import turicreate
```

SFrame can read from CSVs, or load data from it's own format. 

```python
sf = turicreate.SFrame('people-example.csv')

sf = turicreate.SFrame('people_wiki.sframe')
```

## Using SFrame

### Dataframe Operations

You can use many pandas equivalent APIs in SFrame. Like for example, to get a preview of the data

```python
sf # shows a truncated dataframe
```

This will show a few rows and columns, and also show the number of rows and columns in the data. 

Head and tail operations are also equivalent. 

```python
sf.head() # shows the first few rows
sf.tail(10) # shows the last 10 rows. 
```

### Visualisations

One of the biggest advantage of SFrame is the inbuilt easy to use visualisations. 

```python
sf.show() # will show some summary visualisations of the whole dataframe
```

For a single column, you can also use the following. 

```python
sf['age'].show() # will show some summary visualisations of the column. 
```

### Inspecting Columns

You can inspect columns by just using their indices. 

```python
sf['Country'] # will show the number of rows and some example values. 
```

You can also call some inbuilt statistical functions.

```python
sf['age'].mean() # mean
sf['age'].max() # max value
```

### Inspecting Rows

Likewise, you can also access rows with their index values. 

```python
sf[2] # will get the 3rd row
```

### Sorting Columns

You can also sort the columns using the `sort()` function.

```python
sf.sort('text') # returns the dataframe with the sorted column 
```

### Creating New Columns

You can create new columns with a simple syntax. 

```python
sf['Full Name'] = sf['First Name'] + ' ' + sf['Last Name'] # creates a new column based on other column values
```

Its also possible to manipulate column values and get it. 

```python
sf['age'] * sf['age']
```

### `apply()` Function

The `apply()` function syntax in many ways is better than pandas. 

```python
def transform_country(country):
    if country == 'USA':
        return 'United States'
    else:
        return country

sf['Country'].apply(transform_country)
sf['Country'] = sf['Country'].apply(transform_country)
```

