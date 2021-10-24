[Home](README.md)

<br>

# Pandas

<br>

## Readings from [10 minutes to pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html)

<br>

### Object creation

<br>

> First, import both numpy and pandas.

```
import numpy as np

import pandas as pd
```

<br>

> Creating a Series by passing a list of values, letting pandas create a default integer index:

```
s = pd.Series([1, 3, 5, np.nan, 6, 8])
s

# 0    1.0
# 1    3.0
# 2    5.0
# 3    NaN
# 4    6.0
# 5    8.0
# dtype: float64
```

<br>

> Creating a DataFrame by passing a NumPy array, with a datetime index and labeled columns.

```
dates = pd.date_range("20130101", periods=6)
dates

# DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
#                '2013-01-05', '2013-01-06'],
#               dtype='datetime64[ns]', freq='D')

df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))
df
                   # A         B         C         D
# 2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
# 2013-01-02  1.212112 -0.173215  0.119209 -1.044236
# 2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
# 2013-01-04  0.721555 -0.706771 -1.039575  0.271860
# 2013-01-05 -0.424972  0.567020  0.276232 -1.087401
# 2013-01-06 -0.673690  0.113648 -1.478427  0.524988
```
<br>

> Creating a DataFrame by passing a dict of objects that can be converted to series-like `pd.DataFrame`.

> The columns of the resulting DataFrame have different dtypes `df2.dtypes`.

> If you’re using IPython, tab completion for column names (as well as public attributes) is automatically enabled.:

<br>

### Viewing data

<br>

> Use `df.head()`, `df.tail()`.

> Display the index, columns `df.index`, `df.columns`.

> `DataFrame.to_numpy(`) gives a NumPy representation of the underlying data.

> Note that this can be an expensive operation when your DataFrame has columns with different data types, which comes down to a fundamental difference between pandas and NumPy: NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column.

> When you call `DataFrame.to_numpy()`, pandas will find the NumPy dtype that can hold all of the dtypes in the DataFrame.

> This may end up being object, which requires casting every value to a Python object.

> For df, our DataFrame of all floating-point values, `DataFrame.to_numpy()` is fast and doesn’t require copying data `df.to_numpy()`.

> The DataFrame with multiple dtypes, `DataFrame.to_numpy()` is relatively expensive  `df2.to_numpy()`.

> `describe()` shows a quick statistic summary of your data.

> Transposing your data `df.T`.

> Sorting by an axis `df.sort_index(axis=1, ascending=False)`.

> Sorting by values `df.sort_values(by="B")`.

<br>

### Selection

<br>

> While standard Python / NumPy expressions for selecting and setting are intuitive and come in handy for interactive work, for production code, we recommend the optimized pandas data access methods, `.at`, `.iat`, `.loc` and `.iloc`.

<br>

- Getting

> Selecting a single column, which yields a Series, equivalent to df.A `df["A"]`.

> Selecting via [], which slices the rows `df[0:3]`.

<br>

- Selection by label¶

> For getting a cross section using a label `df.loc[dates[0]]`.

> Selecting on a multi-axis by label `df.loc[:, ["A", "B"]]`.

> Showing label slicing, both endpoints are included `df.loc["20130102":"20130104", ["A", "B"]]`.

> Reduction in the dimensions of the returned object `df.loc["20130102", ["A", "B"]]`.

> For getting a scalar value `df.loc[dates[0], "A"]`.

> For getting fast access to a scalar (equivalent to the prior method) `df.at[dates[0], "A"]`.

<br>

- Selection by position

> Select via the position of the passed integers `df.iloc[3]`.

> By integer slices, acting similar to NumPy/Python `df.iloc[3:5, 0:2]`.

> By lists of integer position locations, similar to the NumPy/Python style `df.iloc[[1, 2, 4], [0, 2]]`.

> For slicing rows explicitly `df.iloc[1:3, :]`.

> For slicing columns explicitly `df.iloc[:, 1:3]`.

> For getting a value explicitly `df.iloc[1, 1]`.

> For getting fast access to a scalar (equivalent to the prior method) `df.iat[1, 1]`.

<br>

- Boolean indexing

> Using a single column’s values to select data `df[df["A"] > 0]`.

> Selecting values from a DataFrame where a boolean condition is met `df[df > 0]`.

> Using the isin() method for filtering `df2 = df.copy()`  `df2[df2["E"].isin(["two", "four"])]`.

- Setting

> Setting a new column automatically aligns the data by the indexes `s1 = pd.Series([1, 2, 3, 4, 5, 6], index=pd.date_range("20130102", periods=6))`.

> Setting values by label `df.at[dates[0], "A"] = 0`.

> Setting values by position `df.iat[0, 1] = 0`.

> Setting by assigning with a NumPy array `df.loc[:, "D"] = np.array([5] * len(df))`.

> A `where` operation with setting `df2 = df.copy()`  `df2[df2 > 0] = -df2`.

<br>

### Missing data

<br>

> Pandas primarily uses the value np.nan to represent missing data.

> It is by default not included in computations.

> Reindexing allows you to change/add/delete the index on a specified axis. This returns a copy of the data  `df1 = df.reindex(index=dates[0:4], columns=list(df.columns) + ["E"])` `df1.loc[dates[0] : dates[1], "E"] = 1`.

> To drop any rows that have missing data `df1.dropna(how="any")`.

> Filling missing data `df1.fillna(value=5)`.

> To get the boolean mask where values are nan `pd.isna(df1)`.

<br>

### Operations

<br>

- Stats

> Performing a descriptive statistic `df.mean()`.

> Same operation on the other axis `df.mean(1)`.

> Operating with objects that have different dimensionality and need alignment `s = pd.Series([1, 3, 5, np.nan, 6, 8], index=dates).shift(2)`.

> In addition, pandas automatically broadcasts along the specified dimension `df.sub(s, axis="index")`.

<br>

- Apply

> Applying functions to the data `df.apply(np.cumsum)`  `df.apply(lambda x: x.max() - x.min())`.

<br>

- Histogramming

> `s = pd.Series(np.random.randint(0, 7, size=10))`.

> `s.value_counts()`

<br>

- String Methods

> Series is equipped with a set of string processing methods in the str attribute that make it easy to operate on each element of the array.

> Note that pattern-matching in str generally uses regular expressions by default (and in some cases always uses them). See more at Vectorized String Methods.

> `s = pd.Series(["A", "B", "C", "Aaba", "Baca", np.nan, "CABA", "dog", "cat"])`,  `s.str.lower()`

<br>

### Merge

<br>

- Concat

> pandas provides various facilities for easily combining together Series and DataFrame objects with various kinds of set logic for the indexes and relational algebra functionality in the case of join / merge-type operations.

> Concatenating pandas objects together with `concat()`. `df = pd.DataFrame(np.random.randn(10, 4))`, `pieces = [df[:3], df[3:7], df[7:]]`, `pd.concat(pieces)`.

> Adding a column to a DataFrame is relatively fast. However, adding a row requires a copy, and may be expensive.

<br>

- Join

> SQL style merges. See the Database style joining section.

> `left = pd.DataFrame({"key": ["foo", "foo"], "lval": [1, 2]})`, `right = pd.DataFrame({"key": ["foo", "foo"], "rval": [4, 5]})`, `pd.merge(left, right, on="key")`.

<br>

### Grouping

<br>

- By “group by” we are referring to a process involving one or more of the following steps:
  - Splitting the data into groups based on some criteria
  - Applying a function to each group independently
  - Combining the results into a data structure

> `df = pd.DataFrame(........)`.

> Grouping and then applying the sum() function to the resulting groups `df.groupby("A").sum()`.

> Grouping by multiple columns forms a hierarchical index, and again we can apply the sum() function `df.groupby(["A", "B"]).sum()`.

<br>

### Reshaping

<br>

- Stack

> `tuples = list(....)`, `index = pd.MultiIndex.from_tuples(tuples, names=["first", "second"])`, `df = pd.DataFrame(np.random.randn(8, 2), index=index, columns=["A", "B"])`, `df2 = df[:4]`.

> The `stack()` method “compresses” a level in the DataFrame’s columns `stacked = df2.stack()`.

> With a “stacked” DataFrame or Series (having a MultiIndex as the index), the inverse operation of `stack()` is `unstack()`, which by default unstacks the last level `stacked.unstack()`.

<br>

- Pivot tables

> `df = pd.DataFrame(....)`.

> We can produce pivot tables from this data very easily `pd.pivot_table(df, values="D", index=["A", "B"], columns=["C"])`.

<br>

- Time series

> pandas has simple, powerful, and efficient functionality for performing resampling operations during frequency conversion (e.g., converting secondly data into 5-minutely data).

> `rng = pd.date_range("1/1/2012", periods=100, freq="S")`, `ts = pd.Series(np.random.randint(0, 500, len(rng)), index=rng)`, `ts.resample("5Min").sum()`.

> Time zone representation `rng = pd.date_range("3/6/2012 00:00", periods=5, freq="D")`, `ts = pd.Series(np.random.randn(len(rng)), rng)`, `ts_utc = ts.tz_localize("UTC")`.

> Converting to another time zone `ts_utc.tz_convert("US/Eastern")`.

> Converting between time span representations `rng = pd.date_range("1/1/2012", periods=5, freq="M")`, `ts = pd.Series(np.random.randn(len(rng)), index=rng)`, `ps = ts.to_period()`, `ps.to_timestamp()`.

> Converting between period and timestamp enables some convenient arithmetic functions to be used.

<br>

- Categoricals

> Pandas can include categorical data in a DataFrame `df = pd.DataFrame(.....)`.

> Convert the raw grades to a categorical data type `df["grade"] = df["raw_grade"].astype("category")`, `df["grade"]`.

> Rename the categories to more meaningful names (assigning to `Series.cat.categories()` is in place!) `df["grade"].cat.categories = ["very good", "good", "very bad"]`.

> Reorder the categories and simultaneously add the missing categories (methods under `Series.cat()` return a new Series by default) `df["grade"] = df["grade"].cat.set_categories(...)`, `df["grade"]`.

> Sorting is per order in the categories, not lexical order `df.sort_values(by="grade")`.

> Grouping by a categorical column also shows empty categories `df.groupby("grade").size()`.

<br>

### Plotting

<br>

> We use the standard convention for referencing the matplotlib API `import matplotlib.pyplot as plt`, `plt.close("all")`.

> The close() method is used to close a figure window `ts = pd.Series(np.random.randn(1000), index=pd.date_range("1/1/2000", periods=1000))`, `ts = ts.cumsum()`, `ts.plot();`.

> On a DataFrame, the plot() method is a convenience to plot all of the columns with labels `df = pd.DataFrame(....)`, `df = df.cumsum()`, `plt.figure();`, `df.plot();`, `plt.legend(loc='best');`.

<br>

### Getting data in/out

<br>

- CSV

> Writing to a csv file `df.to_csv("foo.csv")`.

> Reading from a csv file `pd.read_csv("foo.csv")`.

<br>

- HDF5

> Writing to a HDF5 Store `df.to_hdf("foo.h5", "df")`.

> Reading from a HDF5 Store `pd.read_hdf("foo.h5", "df")`.

<br>

- Excel

> Writing to an excel file `df.to_excel("foo.xlsx", sheet_name="Sheet1")`.

> Reading from an excel file `pd.read_excel("foo.xlsx", "Sheet1", index_col=None, na_values=["NA"])`.

<br>

### Gotchas

<br>

> If you are attempting to perform an operation you might see an exception like: 
```

if pd.Series([False, True, False]):
    print("I was true")
Traceback
    ...
ValueError: The truth value of an array is ambiguous. Use a.empty, a.any() or a.all().

```

<br>

## Readings from [Pandas - Getting Started](https://pandas.pydata.org/pandas-docs/stable/getting_started/intro_tutorials/index.html)

<br>

### What kind of data does pandas handle?

<br>

> Import the package, aka import pandas as pd

> A table of data is stored as a pandas DataFrame

> Each column in a DataFrame is a Series

> You can do things by applying a method to a DataFrame or Series


<br>

### How do I read and write tabular data?

<br>

> Getting data in to pandas from many different file formats or data sources is supported by read_* functions.

> Exporting data out of pandas is provided by different to_*methods.

> The head/tail/info methods and the dtypes attribute are convenient for a first check.

<br>

- How do I select a subset of a DataFrame?

<br>

> When selecting subsets of data, square brackets [] are used.

> Inside these brackets, you can use a single column/row label, a list of column/row labels, a slice of labels, a conditional expression or a colon.

> Select specific rows and/or columns using loc when using the row and column names

> Select specific rows and/or columns using iloc when using the positions in the table

> You can assign new values to a selection based on loc/iloc.

<br>

### How to create plots in pandas?

<br>

> The .plot.* methods are applicable on both Series and DataFrames

> By default, each of the columns is plotted as a different element (line, boxplot,…)

> Any plot created by pandas is a Matplotlib object.

<br>

### How to create new columns derived from existing columns?

<br>

> Create a new column by assigning the output to the DataFrame with a new column name in between the [].

> Operations are element-wise, no need to loop over rows.

> Use rename with a dictionary or function to rename row labels or column names.

<br>

### How to calculate summary statistics?

<br>

> Aggregation statistics can be calculated on entire columns or rows

> groupby provides the power of the split-apply-combine pattern

> value_counts is a convenient shortcut to count the number of entries in each category of a variable

<br>

### How to reshape the layout of tables?

<br>

> Sorting by one or more columns is supported by sort_values

> The pivot function is purely restructuring of the data, pivot_table supports aggregations

> The reverse of pivot (long to wide format) is melt (wide to long format)

<br>

### How to combine data from multiple tables?

<br>

> Multiple tables can be concatenated both column-wise and row-wise using the concat function.

> For database-like merging/joining of tables, use the merge function.

<br>

### How to handle time series data with ease?

<br>

> Valid date strings can be converted to datetime objects using to_datetime function or as part of read functions.

> Datetime objects in pandas support calculations, logical operations and convenient date-related properties using the dt accessor.

> A DatetimeIndex contains these date-related properties and supports convenient slicing.

> Resample is a powerful method to change the frequency of a time series.

<br>

### How to manipulate textual data?

<br>

> String methods are available using the str accessor.

> String methods work element-wise and can be used for conditional indexing.

> The replace method is a convenient method to convert values according to a given dictionary.