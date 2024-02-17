# Pandas

## Get basic details about the dataframe

```python
# show first 5 rows
dataframe.head()

# show names of columns
dataframe.info()

# compute summary statistics for numerical columns
# count is the number of msising values in each column
dataframe.describe()

# get tuple of number of rows and columns (ROWS, COLUMNS)
dataframe.shape

# data values
dataframe.values

# labels for columns and rows
dataframe.columns # column names
dataframe.index # row numbers / names
```

## Sorting and Subsetting
