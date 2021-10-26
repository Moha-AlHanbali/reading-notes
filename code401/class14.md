[Home](README.md)

<br>

# Data Visualization

<br>

## Readings from [Matplotlib tutorial](https://github.com/rougier/matplotlib-tutorial)

<br>

### Introduction

<br>

> matplotlib is probably the single most used Python package for 2D-graphics.

> It provides both a very quick way to visualize data from Python and publication-quality figures in many formats.

- IPython and the pylab mode

> IPython is an enhanced interactive Python shell that has lots of interesting features including named inputs and outputs, access to shell commands, improved debugging and much more. 

> When we start it with the command line argument -pylab (--pylab since IPython version 0.12), it allows interactive matplotlib sessions that have Matlab/Mathematica-like functionality.

- pyplot

> pyplot provides a convenient interface to the matplotlib object-oriented plotting library.

> It is modeled closely after Matlab(TM).

> Therefore, the majority of plotting commands in pyplot have Matlab(TM) analogs with similar arguments.

<br>

### Simple plot

<br>

> Matplotlib comes with a set of default settings that allow customizing all kinds of properties.

> You can control the defaults of almost every property in matplotlib: figure size and dpi, line width, color and style, axes, axis and grid properties, text and font properties and so on. While matplotlib defaults are rather good in most cases, you may want to modify some properties for specific cases.

- Changing colors and line widths

> `plt.figure(figsize=(10,6), dpi=80)`

> `plt.plot(X, C, color="blue", linewidth=2.5, linestyle="-")`

- Setting limits

> `plt.xlim(X.min()*1.1, X.max()*1.1)`

- Setting ticks

> `plt.xticks( [-np.pi, -np.pi/2, 0, np.pi/2, np.pi])`

> `plt.yticks([-1, 0, +1])`

- Setting tick labels

> `plt.xticks([.....])`

> `plt.yticks([.....])`

- Adding a legend

> `plt.legend(loc='upper left', frameon=False)`

<br>

### Figures, Subplots, Axes and Ticks

<br>

- Figures

> A figure is the windows in the GUI that has "Figure #" as title. Figures are numbered starting from 1 as opposed to the normal Python way starting from 0.

- Subplots

> With subplot you can arrange plots in a regular grid.

> You need to specify the number of rows and columns and the number of the plot. Note that the gridspec command is a more powerful alternative.

- Axes

> Axes are very similar to subplots but allow placement of plots at any location in the figure. So if we want to put a smaller plot inside a bigger one we do so with axes.

- Ticks

> Well formatted ticks are an important part of publishing-ready figures.

> Matplotlib provides a totally configurable system for ticks. There are tick locators to specify where ticks should appear and tick formatters to give ticks the appearance you want. 

> Major and minor ticks can be located and formatted independently from each other.

<br>

### Animation

<br>

> The most easy way to make an animation in matplotlib is to declare a FuncAnimation object that specifies to matplotlib what is the figure to update, what is the update function and what is the delay between frames.

- Drip drop

> A very simple rain effect can be obtained by having small growing rings randomly positioned over a figure.

> Of course, they won't grow forever since the wave is supposed to damp with time.

> To simulate that, we can use a more and more transparent color as the ring is growing, up to the point where it is no more visible. At this point, we remove the ring and create a new one.

> Next, we need to create several rings. For this, we can use the scatter plot object that is generally used to visualize points cloud, but we can also use it to draw rings by specifying we don't have a facecolor.

> We also have to take care of initial size and color for each ring such that we have all sizes between a minimum and a maximum size. In addition, we need to make sure the largest ring is almost transparent.

<br>

## Readings from [Python For Data Science Cheat Sheet - Seaborn](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Python_Seaborn_Cheat_Sheet.pdf)

<br>

### Introduction

<br>


> The Python visualization library Seaborn is based on matplotlib and provides a high-level interface for drawing attractive statistical graphics.

> Make use of the following aliases to import the libraries:

```

import matplotlib.pyplot as plt
import seaborn as sns

```
<br>

- The basic steps to creating plots with Seaborn are:
 1. Prepare some data
 2. Control figure aesthetics
 3. Plot with Seaborn
 4. Further customize your plot

<br>

### Data

<br>

> Seaborn also offers built-in data sets

> `variable = sns.load_dataset("data")`

<br>

### Figure Aesthetics

<br>

> Create a figure and one subplot

> `f, ax = plt.subplots(figsize=(5,6))`

- Seaborn styles

```
 sns.set()                    #(Re)set the seaborn default
 sns.set_style("whitegrid")   #Set the matplotlib parameters
 sns.set_style("ticks",
{"xtick.major.size":8,           #Set the matplotlib parameters 
"ytick.major.size":8})
 sns.axes_style("whitegrid")  #Return a dict of params or use with with to temporarily set the style
```
<br>

- Context Functions

> `sns.set_context("context")`

- Color Palette

> `sns.set_palette("set_palette",int) `

<br>

### Plotting With Seaborn

<br>

- Axis Grids

> ` g = sns.FacetGrid(data, col = 'column', row = 'row')`

> `sns.lmplot(x = '', y = '', hue = '', data= data)`

- Regression Plots

> `sns.regplot(x="x", y="y", data=data,ax=ax)`

<br>

### 4Further Customizations

<br>

> ` plt.title("title")`

> `plt.ylabel(""ylabel")`

> `plt.xlim(0, 100)`

<br>

### Show or Save Plot

<br>

> `plt.show() `

> `plt.savefig("foo.png")`

> `plt.cla()`

> `plt.clf() `

> `plt.close()`
