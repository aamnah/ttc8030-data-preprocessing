# Pandas

- [10 minutes to pandas](https://pandas.pydata.org/docs/user_guide/10min.html)

## DataFrame generation

Read files as a DataFrame:

```python
import pandas as pd
df = pd.read_csv("file_path_or_url")
```

DataFrame generation:

```python
first_column = [7,2,6,23,90] 
second_column = ["value1", "value2", "value3", "value4", "value5"]

# DataFrame genertion 
generated_dataframe = pd.DataFrame({"column1":first_column, "column2":second_column})

generated_dataframe
```


## Get basic details about the dataframe

```python
# show first rows (default: 5)
df.head()

# show last rows (default: 5)
df.tail()
# Show the last three rows
df.tail(3)

# show names of columns
df.info()

# compute summary statistics for numerical columns
# count is the number of msising values in each column
# describe() shows a quick statistic summary of your data
df.describe()

# get tuple of number of rows and columns (ROWS, COLUMNS)
df.shape

# data values
df.values

# labels for columns and rows
df.columns # column names

## The index (row labels) of the DataFrame.
df.index # row numbers / names
```

```python
# by default only first and last 5 rows are shown
pd.set_option('display.max.rows') # show max rows
pd.set_option('display.max.rows', 235) # show 235 rows

pd.set_option('display.max.columns')
pd.set_option('display.max.columns', 30)
```

## Sorting and Subsetting

```python
# sorting a column
dataframe.sort_values("weight_kg")

# sorting in descending order
dataframe.sort_values("weight_kg", ascending=False)

# sorting by multiple variables
dataframe.sort_values("weight_kg", "height_cm")
dataframe.sort_values(["weight_kg", "height_cm"], ascneding=[True, False])
```

```python
# subsetting columns
dataframe["column_name"]

dataframe[["breed", "height_cm"]]
# outer square brackets are responsible for subsetting teh dataframe
# inner square brackets are creating a list of column names to subset

cols_to_subset = ["breed", "height_cm"]
dataframe[cols_to_subset]
```

```python
# subsetting rows
dataframe["height_cm"] > 50 # logical consition to filter against, result is a Boolean value for every row
dataframe[dataframe["height_cm"] > 50] # result is a subset of rows that fulfill that logical condition


# subset rows based on text data
dataframe[dataframe["breed" == "Labrador"]]
# outer square brackets are responsible for subsetting teh dataframe
# inner square brackets are creating a list of column names to subset

# subset based on dates
dataframe[dataframe["date_of_birth" < "2015-01-01"]]

# subset based on multiple conditions
is_lab = dogs["breed"] == "Labrador"
is_brown = dogs["color"] == "Brown"
dogs[is_lab & is_brown]

# same as above, but you need to wrap conditions in parantheses
dogs[(dogs["breed"] == "Labrador") & (dogs["color"] == "Brown")]

is_black_or_brown = dogs["color"].isin(["Black", "Brown"])
dogs[is_black_or_brown]
```

## Adding new columns
aka _Mutating_/_Transforming_ a dataframe and _Feature Engineering_


```python
dogs["height_m"] = dogs["height_cm" / 100]

#  BMI = wieght in kg / (height in m)²
dogs["bmi"] = dogs["weight_kg"] / dogs["height_m"] ** 2

# skinny, tall dogs
bmi_lt_100 = dogs[dogs["bmi"] < 100]
bmi_lt_100_height = bmi_lt_100.sort_values("height_cm", ascending=False)
bmi_lt_100_height[["name", "height_cm", "bmi"]]
```

## Looking things up
`.loc()` and `.iloc()`

- `.loc()` selection by label, looks for actual text 
- `.iloc()` selection by position, looks for index integer

```python
df.iloc[0:2, 0:3] # first 2 rows, and first 3 columns
df.iloc[0] # value of first cell

```

```python
# select all rows in all columns, i.e. entire dataframe
car_data.loc[:,:]

# last value of column labelled 'column1'
df.column1.iloc[-1]

# Show the rows from 3 to 8 (inclusive) of car data
car_data[3:9]

# Show the last five rows of car data in reverse order
# [-5:] chooses the rows starting from the fifth last row till the end 
# [::-1] reverses the output
car_data[-5:][::-1]

# Select Horsepower information of Ford Torino using .loc
print(car_data.loc[13,"Horsepower"])

# Select Horsepower information of Ford Torino using .iloc
print(car_data.iloc[13,4])
```

## Reading in data

```python
import pandas as pd

# CSV
cars_df = pd.read_csv("./data/cars.csv")
countries_df = pd.read_csv(r"C:\Users\foo\OneDrive\Documents\data\countries.csv") # r at the beginning says read the file path as raw string
iris_df = pd.read_csv("https://raw.githubusercontent.com/mwaskom/seaborn-data/master/iris.csv")

# Text
# df = read_csv(r"C:\Users\foo\OneDrive\Documents\data\countries.txt", sep="\t")
df = read_table(r"C:\Users\foo\OneDrive\Documents\data\countries.txt", sep=",")

# JSON
json_df = pd.read_json("./data/cars.json")

# Excel
excel_df = pd.read_excel("./data/cars.xlsx") # by default reads only 1st sheet
excel_sheet_df = pd.read_excel("./data/cars.xlsx", sheet_name = 'Sheet2') 
```

## Delete / Drop

```python
# Assuming df is your DataFrame with the "Unnamed: 0" column
# To drop the column in-place (modify the original DataFrame):
# df.drop(columns=df.columns[0], inplace=True)
df.drop(columns="Unnamed: 0", inplace=True)

# Alternatively, to create a new DataFrame without the "Unnamed: 0" column:
df_without_unnamed = df.drop(columns="Unnamed: 0")
```

```python
# Remove the first row (index number 0) from the DataFrame and save the changes for the new DataFrame
# This would be the same as car_data = car_data.drop(0)
car_data.drop(0, inplace=True)
car_data
```

```python
# Delete rows if the value 0.2 or less appears in the column `column1`
# .index gets the index/label of a row

# step by step
criteria = df['column1'] <= 0.2 # this criteria must be met
rows = df.loc[criteria].index # these rows match the criteria
df.drop(rows, inplace=True) # drop the rows matching the criteria

# one-liner
df.drop(df.loc[df['column1'] <= 0.2].index, inplace=True)
```


```python
# select rows with NaN values in all columns
df[df.isna().any(axis=1)] 
```




```python
# Add a row (to an existing dataframe)
df.loc[len(df.index)] = ['Bart', 12, 35, 31]
```