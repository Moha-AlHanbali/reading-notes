[Home](README.md)

<br>

# Linear Regressions

<br>

## Readings from [How to run Linear regression in Python scikit-Learn](http://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/)

<br>

### Overview

<br>

> Scikit-learn is a powerful Python module for machine learning.

> It contains function for regression, classification, clustering, model selection and dimensionality reduction.

<br>

### Exploring Data Set

<br>

> The first step is to import the required Python libraries into Ipython Notebook.

```
%matplotlib inline

import numpy as np
import pandas as pd
import spicy.stats as stats
import matplotlib as plt
import sklearn
from source import data_set
```

<br>

> This data set is available in sklearn Python module, so I will access it using scikitlearn. I am going to import Boston data set into Ipython notebook and store it in a variable called boston.

> You can explore the keys of this dictionary `data_set.keys()`.

> `data_set.data.shape`.

> `print data_set.key`.

<br>

> Convert data_set into a pandas data frame `df = pd.DataFrame(data_set)`.

> `data_set.key` contains the data `data_set,key[:5]`.

> Add these to the df data frame `df['name'] = data_set,key`.

<br>

### Scikit Learn

<br>

> Import linear regression from sci-kit learn module. 

>Then drop a data column as we only the parameters as my X values.

> We are going to store linear regression object in a variable called lm.

```
from sklearn.linear_model import LinearRegression
x = df.drop('name', axis = 1)
lm = Linear Regression
lm
```

<br>

- Important functions to keep in mind while fitting a linear regression model are:
  - lm.fit() -> fits a linear model
  - lm.predict() -> Predict Y using the linear model with estimated coefficients
  - lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.

<br>

### Fitting a Linear Model

<br>

> `lm.fit(X, df.DATA)`

>  `LinearRegression(copy_X=True, fit_intercept=True, normalize=False)`

<br>

### Training and validation data sets

<br>

> In practice you wont implement linear regression on the entire data set, you will have to split the data sets into training and test data sets.

> So that you train your model on training data and see how well it performed on test data.


<br>

### How to do train-test split

<br>

> Scikit learn provides a function called train_test_split to do that.

<br>

### Residual Plots

<br>

> Residual plots are a good way to visualize the errors in your data.

> If you have done a good job then your data should be randomly scattered around line zero.

> If you see structure in your data, that means your model is not capturing some thing.

> May be there is a interaction between 2 variables that you are not considering, or may be you are measuring time dependent data.

> If you get some structure in your data, you should go back to your model and check whether you are doing a good job with your parameters.

<br>

## Readings from [Linear Regression in Python](https://realpython.com/linear-regression-in-python/)

<br>

### What Is Regression?

<br>

> Regression searches for relationships among variables.

> For example, you can observe several employees of some company and try to understand how their salaries depend on the features, such as experience, level of education, role, city they work in, and so on.

> This is a regression problem where data related to each employee represent one observation.

> The presumption is that the experience, education, role, and city are the independent features, while the salary depends on them.

> Generally, in regression analysis, you usually consider some phenomenon of interest and have a number of observations.

> Each observation has two or more features.

> Following the assumption that (at least) one of the features depends on the others, you try to establish a relation among them.

> You need to find a function that maps some features or variables to others sufficiently well.

> The dependent features are called the dependent variables, outputs, or responses.

> The independent features are called the independent variables, inputs, or predictors.

> Regression problems usually have one continuous and unbounded dependent variable.

> The inputs, however, can be continuous, discrete, or even categorical data such as gender, nationality, brand, and so on.

> It is a common practice to denote the outputs with 𝑦 and inputs with 𝑥.

> If there are two or more independent variables, they can be represented as the vector 𝐱 = (𝑥₁, …, 𝑥ᵣ), where 𝑟 is the number of inputs.

<br>

### When Do You Need Regression?

<br>

> Typically, you need regression to answer whether and how some phenomenon influences the other or how several variables are related.

> For example, you can use it to determine if and to what extent the experience or gender impact salaries.

> Regression is also useful when you want to forecast a response using a new set of predictors.

> For example, you could try to predict electricity consumption of a household for the next hour given the outdoor temperature, time of day, and number of residents in that household.

<br>

### Linear Regression

<br>

> Linear regression is probably one of the most important and widely used regression techniques. I

> One of its main advantages is the ease of interpreting results.

<br>

- Problem Formulation

> When implementing linear regression of some dependent variable 𝑦 on the set of independent variables `𝐱 = (𝑥₁, …, 𝑥ᵣ)`, where `𝑟` is the number of predictors, you assume a linear relationship between `𝑦` and `𝐱: 𝑦 = 𝛽₀ + 𝛽₁𝑥₁ + ⋯ + 𝛽ᵣ𝑥ᵣ + 𝜀`. This equation is the regression equation.

>` 𝛽₀, 𝛽₁, …, 𝛽ᵣ` are the regression coefficients, and 𝜀 is the random error.

> Linear regression calculates the estimators of the regression coefficients or simply the predicted weights, denoted with `𝑏₀, 𝑏₁, …, 𝑏ᵣ`.

> They define the estimated regression function `𝑓(𝐱) = 𝑏₀ + 𝑏₁𝑥₁ + ⋯ + 𝑏ᵣ𝑥ᵣ`.

> This function should capture the dependencies between the inputs and output sufficiently well.

> The estimated or predicted response, `𝑓(𝐱ᵢ)`, for each observation `𝑖 = 1, …, 𝑛`, should be as close as possible to the corresponding actual response `𝑦ᵢ`.

> The differences `𝑦ᵢ - 𝑓(𝐱ᵢ)` for all observations `𝑖 = 1, …, 𝑛`, are called the residuals. Regression is about determining the best predicted weights, that is the weights corresponding to the smallest residuals.

> To get the best weights, you usually minimize the sum of squared residuals (SSR) for all observations `𝑖 = 1, …, 𝑛: SSR = Σᵢ(𝑦ᵢ - 𝑓(𝐱ᵢ))²`. This approach is called the method of ordinary least squares.

<br>

- Regression Performance

> The variation of actual responses `𝑦ᵢ, 𝑖 = 1, …, 𝑛`, occurs partly due to the dependence on the predictors `𝐱ᵢ`.

> However, there is also an additional inherent variance of the output.

> The coefficient of determination, denoted as `𝑅²`, tells you which amount of variation in 𝑦 can be explained by the dependence on 𝐱 using the particular regression model.

> Larger `𝑅²` indicates a better fit and means that the model can better explain the variation of the output with different inputs.

> The value `𝑅² = 1` corresponds to `SSR = 0`, that is to the perfect fit since the values of predicted and actual responses fit completely to each other.

<br>

### Underfitting and Overfitting

<br>

> One very important question that might arise when you’re implementing polynomial regression is related to the choice of the optimal degree of the polynomial regression function.

> There is no straightforward rule for doing this.

> It depends on the case. You should, however, be aware of two problems that might follow the choice of the degree: underfitting and overfitting.

> Underfitting occurs when a model can’t accurately capture the dependencies among data, usually as a consequence of its own simplicity.

> It often yields a low `𝑅²` with known data and bad generalization capabilities when applied with new data.

> Overfitting happens when a model learns both dependencies among data and random fluctuations. In other words, a model learns the existing data too well.

> Complex models, which have many features or terms, are often prone to overfitting.

> When applied to known data, such models usually yield high `𝑅²`.

> However, they often don’t generalize well and have significantly lower `𝑅²` when used with new data.

<br>

### Python Packages for Linear Regression

<br>

> The package NumPy is a fundamental Python scientific package that allows many high-performance operations on single- and multi-dimensional arrays. It also offers many mathematical routines. Of course, it’s open source.

> The package scikit-learn is a widely used Python library for machine learning, built on top of NumPy and some other packages.

> It provides the means for preprocessing data, reducing dimensionality, implementing regression, classification, clustering, and more. Like NumPy, scikit-learn is also open source.

<br>

- Simple Linear Regression With scikit-learn

- There are five basic steps when you’re implementing linear regression:
  - Import the packages and classes you need.
  - Provide data to work with and eventually do appropriate transformations.
  - Create a regression model and fit it with existing data.
  - Check the results of model fitting to know whether the model is satisfactory.
  - Apply the model for predictions.

```

import numpy as np
from sklearn.linear_model import LinearRegression

x = np.array([5, 15, 25, 35, 45, 55]).reshape((-1, 1))
y = np.array([5, 20, 14, 32, 22, 38])

model = LinearRegression()

model.fit(x, y)

model = LinearRegression().fit(x, y)

r_sq = model.score(x, y)

new_model = LinearRegression().fit(x, y.reshape((-1, 1)))

y_pred = model.predict(x)

y_pred = model.intercept_ + model.coef_ * x

x_new = np.arange(5).reshape((-1, 1))


```
<br>

> `model = LinearRegression()` This statement creates the variable model as the instance of LinearRegression. You can provide several optional parameters to LinearRegression:
  - fit_intercept is a Boolean (True by default) that decides whether to calculate the intercept 𝑏₀ (True) or consider it equal to zero (False).
  - normalize is a Boolean (False by default) that decides whether to normalize the input variables (True) or not (False).
  - copy_X is a Boolean (True by default) that decides whether to copy (True) or overwrite the input variables (False).
  - n_jobs is an integer or None (default) and represents the number of jobs used in parallel computation. None usually means one job and -1 to use all processors.

<br>

### Beyond Linear Regression

<br>

> Linear regression is sometimes not appropriate, especially for non-linear models of high complexity.

> Fortunately, there are other regression techniques suitable for the cases where linear regression doesn’t work well.

> Some of them are support vector machines, decision trees, random forest, and neural networks.

> There are numerous Python libraries for regression using these techniques.

> Most of them are free and open-source. That’s one of the reasons why Python is among the main programming languages for machine learning.

> The package scikit-learn provides the means for using other regression techniques in a very similar way to what you’ve seen.

> It contains the classes for support vector machines, decision trees, random forest, and more, with the methods .fit(), .predict(), .score() and so on.

<br>

### Conclusion

<br>

> You now know what linear regression is and how you can implement it with Python and three open-source packages: NumPy, scikit-learn, and statsmodels.

> You use NumPy for handling arrays.

> Linear regression is implemented with the following:
  - scikit-learn if you don’t need detailed results and want to use the approach consistent with other regression techniques
  - statsmodels if you need the advanced statistical parameters of a model

> Both approaches are worth learning how to use and exploring further. The links in this article can be very useful for that.

