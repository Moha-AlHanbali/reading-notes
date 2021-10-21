[Home](README.md)

<br>

# Data Analysis

<br>

## Readings from [What is JupyterLab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)

<br>

### Overview

<br>

> JupyterLab is a next-generation web-based user interface for Project Jupyter.

<br>

> JupyterLab enables you to work with documents and activities such as Jupyter notebooks, text editors, terminals, and custom components in a flexible, integrated, and extensible manner. 

> You can arrange multiple documents and activities side by side in the work area using tabs and splitters.

> Documents and activities integrate with each other, enabling new workflows for interactive computing.

- Code Consoles
  - Provide transient scratchpads for running code interactively, with full support for rich output. A code console can be linked to a notebook kernel as a computation log from the notebook, for example.
- Kernel-backed documents 
  - Enable code in any text file (Markdown, Python, R, LaTeX, etc.) to be run interactively in any Jupyter kernel.
- Notebook cell 
  - Outputs can be mirrored into their own tab, side by side with the notebook, enabling simple dashboards with interactive controls backed by a kernel.
- Multiple views of documents with different editors or viewers enable live editing of documents reflected in other viewers. For example, it is easy to have live preview of Markdown, Delimiter-separated Values, or Vega/Vega-Lite documents.

> JupyterLab  offers a unified model for viewing and handling data formats.

> JupyterLab understands many file formats (`images`, `CSV`, `JSON`, `Markdown`, `PDF`, `Vega`, `Vega-Lite`, etc.) and can also display rich kernel output in these formats.

<br>

<br>

## Readings from [NumPy Tutorial: Data Analysis with Python](https://www.dataquest.io/blog/numpy-tutorial-python/)

<br>

### Overview

<br>

> NumPy is a commonly used Python data analysis package.

> By using NumPy, you can speed up your workflow, and interface with other packages in the Python ecosystem, like scikit-learn, that use NumPy under the hood. 

<br>

### Lists Of Lists for CSV Data

<br>

> Before using NumPy, we’ll first try to work with the data using Python and the csv package.

> We can read in the file using the csv.reader object, which will allow us to read in and split up all the content from the ssv file.

<br>


```
Import csv
with open('variablesomething-red.csv', 'r') as f:
    variable = list(csv.reader(f, delimiter=';'))
```

<br>

> Once we’ve read in the data, we can print out the first 3 rows

<br>

```
print(variable[:3])
```

<br>

> The data has been read into a list of lists.

> Each inner list is a row from the ssv file. As you may have noticed, each item in the entire list of lists is represented as a string, which will make it harder to do computations.

<br>

> You can extract the last element from each row after the header.

> Convert each extracted element to a float.

> Assign all the extracted elements to the list something.

> Divide the sum of all the elements in something by the total number of elements in something to the get the mean.

<br>

```
something =
[float(item[-1]) for item in variable[1:]]
sum(something) / len(something)
```

<br>

### Numpy 2-Dimensional Arrays

<br>

> A 2-dimensional array is also known as a matrix, and is something you should be familiar with.

> A matrix has rows and columns.

> By specifying a row number and a column number, we’re able to extract an element from a matrix.

> In a NumPy array, the number of dimensions is called the rank, and each dimension is called an axis.

> So the rows are the first axis, and the columns are the second axis.

<br>

### Creating A NumPy Array

<br>

> We can create a NumPy array using the numpy.array function.

> If we pass in a list of lists, it will automatically create a NumPy array with the same number of rows and columns.

> Because we want all of the elements in the array to be float elements for easy computation, we’ll leave off the header row, which contains strings.

> One of the limitations of NumPy is that all the elements in an array have to be of the same type, so if we include the header row, all the elements in the array will be read in as strings.

> Because we want to be able to do computations like find the average quality of the some data, we need the elements to all be floats.

> If we display the data, we’ll now get a NumPy array.

> We can check the number of rows and columns in our data using the shape property of NumPy arrays.

<br>

```
import numpy as np
variable = np.array(variable[1:], dtype=np.float)

variable
```

<br>

### Alternative NumPy Array Creation Methods

<br>

> There are a variety of methods that you can use to create NumPy arrays.

> To start with, you can create an array where every element is zero.

> The below code will create an array with 3 rows and 4 columns, where every element is 0, using numpy.zeros.

> It’s useful to create an array with all zero elements in cases when you need an array of fixed size, but don’t have any values for it yet.

> You can also create an array where each element is a random number using numpy.random.rand.

> Creating arrays full of random numbers can be useful when you want to quickly test your code with sample arrays.

<br>

```
import numpy as np

empty_array = np.zeros((3,4))

empty_array
```

<br>

### Using NumPy To Read In Files

<br>

> It’s possible to use NumPy to directly read csv or other files into arrays. We can do this using the numpy.genfromtxt function.

> We can use it to read in our initial data.

<br>

```
variable = np.genfromtxt("variablesomething-red.csv", delimiter=";", skip_header=1)

```

<br>

### Indexing NumPy Arrays

<br>

> We can use array indexing to select individual elements, groups of elements, or entire rows and columns.

> One important thing to keep in mind is that just like Python lists, NumPy is zero-indexed, meaning that the index of the first row is 0, and the index of the first column is 0.

> If we want to work with the fourth row, we’d use index 3, if we want to work with the second row, we’d use index 1, and so on.

> Since we’re working with a 2-dimensional array in NumPy, we specify 2 indexes to retrieve an element.

> The first index is the row, or axis 1, index, and the second index is the column, or axis 2, index. Any element in dataset can be retrieved using 2 indexes.

<br>

### Slicing NumPy Arrays

<br>

> If we instead want to select the first three items from the fourth column, we can do it using a colon (:).

> A colon indicates that we want to select all the elements from the starting index up to but not including the ending index.

> This is also known as a slice.

> Just like with list slicing, it’s possible to omit the 0 to just retrieve all the elements from the beginning up to element 3.

> We can select an entire column by specifying that we want all the elements, from the first to the last.

> We specify this by just using the colon (:), with no starting or ending indices.

<br>

### Assigning Values To NumPy Arrays

<br>

> We can also use indexing to assign values to certain elements in arrays. We can do this by assigning directly to the indexed value.

> We can do the same for slices. To overwrite an entire column.

<br>

### 1-Dimensional NumPy Arrays

<br>

> NumPy is a package for working with multidimensional arrays.

> One of the most common types of multidimensional arrays is the 1-dimensional array. 

> When we sliced variable, we retrieved a 1-dimensional array.

> A 1-dimensional array only needs a single index to retrieve an element.

> Each row and column in a 2-dimensional array is a 1-dimensional array.

> Just like a list of lists is analogous to a 2-dimensional array, a single list is analogous to a 1-dimensional array.

> If we slice variable and only retrieve the third row, we get a 1-dimensional array.

> Most NumPy functions that we’ve worked with, such as numpy.random.rand, can be used with multidimensional arrays.

> Here’s how we’d use numpy.random.rand to generate a random vector.

> Previously, when we called np.random.rand, we passed in a shape for a 2-dimensional array, so the result was a 2-dimensional array.

> This time, we passed in a shape for a single dimensional array.

> The shape specifies the number of dimensions, and the size of the array in each dimension. A shape of (10,10) will be a 2-dimensional array with 10 rows and 10 columns. A shape of (10,) will be a 1-dimensional array with 10 elements.

<br>

### N-Dimensional NumPy Arrays

<br>

> This doesn’t happen extremely often, but there are cases when you’ll want to deal with arrays that have greater than 3 dimensions.

> One way to think of this is as a list of lists of lists.

> Let’s say we want to store the monthly earnings of a store, but we want to be able to quickly lookup the results for a quarter, and for a year.

> We can retrieve the earnings from January of the first year by calling earnings[0][0][0].

> We now need three indexes to retrieve a single element.

> A three-dimensional array in NumPy is much the same. In fact, we can convert earnings to an array and then get the earnings for January of the first year.

> Adding more dimensions can make it much easier to query your data if it’s organized in a certain way.

> As we go from 3-dimensional arrays to 4-dimensional and larger arrays, the same properties apply, and they can be indexed and sliced in the same ways.


<br>

```
earnings = [
    [
        [500,505,490],
        [810,450,678],
        [234,897,430],
        [560,1023,640]
    ],
    [
        [600,605,490],
        [345,900,1000],
        [780,730,710],
        [670,540,324]
    ]
]

earnings = np.array(earnings)
earnings[0,0,0] # 500

earnings.shape # (2, 4, 3)

earnings[:,0,0] # array([500, 600])

earnings[:,0,:] # array([[500, 505, 490],
                        [600, 605, 490]])

```

<br>

### NumPy Data Types

<br>

> NumPy stores values using its own data types, which are distinct from Python types like float and str.

> This is because the core of NumPy is written in a programming language called C, which stores data differently than the Python data types.

> NumPy data types map between Python and C, allowing us to use NumPy arrays without any conversion hitches.

> You can find the data type of a NumPy array by accessing the dtype property.

- NumPy has several different data types, which mostly map to Python data types, like float, and str.
  - float 
    - numeric floating point data.
  - int 
    - integer data.
  - string 
    - character data.
  - object 
    - Python objects.

> Data types additionally end with a suffix that indicates how many bits of memory they take up. So int32 is a 32 bit integer data type, and float64 is a 64 bit float data type.

<br>

### Converting Data Types

<br>

> You can use the numpy.ndarray.astype method to convert an array to a different type.

> The method will actually copy the array, and return a new array with the specified data type.

> As you can see above, all of the items in the resulting array are integers.

> Several Python data types, including float, int, and string, can be used with NumPy, and are automatically converted to NumPy data types.

<br>

### NumPy Array Operations

<br>

> NumPy makes it simple to perform mathematical operations on arrays.

> This is one of the primary advantages of NumPy, and makes it quite easy to do computations.

<br>

- Single Array Math

> If you do any of the basic mathematical operations (/, *, -, +, ^) with an array and a value, it will apply the operation to each of the elements in the array.

> Note that the above operation won’t change the array — it will return a new 1-dimensional array where 10 has been added to each element in the quality column of it.

<br>

- Multiple Array Math

> It’s also possible to do mathematical operations between arrays.

> This will apply the operation to pairs of elements.

> For example, if we add the quality column to itself.

> Note that this is equivalent to array[11] * 2 — this is because NumPy adds each pair of elements.

> The first element in the first array is added to the first element in the second array, the second to the second, and so on.

> We can also use this to multiply arrays.

<br>

- Broadcasting

> Unless the arrays that you’re operating on are the exact same size, it’s not possible to do elementwise operations.

> In cases like this, NumPy performs broadcasting to try to match up elements.

- Essentially, broadcasting involves a few steps:
  - The last dimension of each array is compared.
    - If the dimension lengths are equal, or one of the dimensions is of length 1, then we keep going.
    - If the dimension lengths aren’t equal, and none of the dimensions have length 1, then there’s an error.
  - Continue checking dimensions until the shortest array is out of dimensions.

<br>

### NumPy Array Methods

<br>

> NumPy also has several methods that you can use for more complex calculations on arrays.

> An example of this is the numpy.ndarray.sum method.

- There are several other methods that behave like the sum method:
  - numpy.ndarray.mean 
    - finds the mean of an array.
  - numpy.ndarray.std 
    - finds the standard deviation of an array.
  - numpy.ndarray.min 
    - finds the minimum value in an array.
  - numpy.ndarray.max 
    - finds the maximum value in an arra

<br>

### NumPy Array Comparisons

<br>

> NumPy makes it possible to test to see if rows match certain values using mathematical comparison operations like <, >, >=, <=, and ==.

<br>

- Subsetting

> One of the powerful things we can do with a Boolean array and a NumPy array is select only certain rows or columns in the NumPy array. 

> We select only the rows where a column contains a True value, and all of the columns.

> This subsetting makes it simple to filter arrays for certain criteria.

> In order to specify multiple conditions, we have to place each condition in parentheses, and separate conditions with an ampersand (&).

<br>

### Reshaping NumPy Arrays

<br>

> We can change the shape of arrays while still preserving all of their elements.

> This often can make it easier to access array elements.

> The simplest reshaping is to flip the axes, so rows become columns, and vice versa. We can accomplish this with the numpy.transpose function.

> We can use the numpy.ravel function to turn an array into a one-dimensional representation. It will essentially flatten an array into a long sequence of values.

<br>

- Combining NumPy Arrays

> With NumPy, it’s very common to combine multiple arrays into a single unified array.

> We can use numpy.vstack to vertically stack multiple arrays.

> Think of it like the second arrays’s items being added as new rows to the first array.
