[Home](README.md)

<br>

# Game of Greed 4

<br>

## Readings from [Enriching Your Python Classes With Dunder (Magic, Special) Methods](https://dbader.org/blog/python-dunder-methods)

<br>

### What Are Dunder Methods?

<br>

> In Python, special methods are a set of predefined methods you can use to enrich your classes.

> They are easy to recognize because they start and end with double underscores, for example` __init__` or `__str__`.

> Pythonistas adopted the term dunder methods, a short form of double under.

> These dunders or special methods in Python are also sometimes called magic methods.

> Dunder methods let you emulate the behavior of built-in types.

<br>

### Object Initialization: `__init__`

<br>

> Right upon starting my class I already need a special method.

> To construct account objects from the Account class I need a constructor which in Python is the `__init__` dunder.

> The constructor takes care of setting up the object. In this case it receives the owner name, an optional start amount and defines an internal transactions list to keep track of deposits and withdrawals.

<br>

### Object Representation: `__str__`, `__repr__`

<br>

> It’s common practice in Python to provide a string representation of your object for the consumer of your class (a bit like API documentation.)

- There are two ways to do this using dunder methods:
  - `__repr__`
    - The “official” string representation of an object. This is how you would make an object of the class. The goal of `__repr__` is to be unambiguous.
  - `__str__`
    - The “informal” or nicely printable string representation of an object. This is for the enduser.

> If you don’t want to hardcode `class ClassName` as the name for the class you can also use `self.__class__.__name__` to access it programmatically.

<br>

### Iteration: `__len__`, `__getitem__`, `__reversed__`

<br>

- Use `__len__` to get the length of a class.

- Use `__getitem__` to get the index of an item in class.

- Use `__reversed__` to iterate in reversed manner.

<br>

### Operator Overloading for Comparing Accounts: `__eq__`, `__lt__`

<br>

> Implement comparison dunders and inherit them from a parent class.

> Use `__eq__` and `__lt__` to compare (equals and less than) classes.

<br>

### Operator Overloading for Merging Accounts: `__add__`

<br>

> In Python, everything is an object.

> We are completely fine adding two integers or two strings with the + (plus) operator.

<br>

> Implement `__add__` to be able to merge two class instances.

> The expected behavior would be to merge all attributes together.

<br>

### Callable Python Objects: `__call__`

<br>

> You can make an object callable like a regular function by adding the `__call__` dunder method.

> A class probably wouldn’t print to the console when you use the function call syntax on one of its instances.

> In general, the downside of having a `__call__` method on your objects is that it can be hard to see what the purpose of calling the object is.

> Most of the time it’s therefore better to add an explicit method to the class.

<br>

### Context Manager Support and the With Statement: `__enter__`, `__exit__`

<br>

> A context manager is a simple “protocol” (or interface) that your object needs to follow so it can be used with the with statement.

> Basically all you need to do is add `__enter__` and `__exit__` methods to an object if you want it to function as a context manager.

<br>

## Readings from [Tutorial: Basic Statistics in Python — Probability](hhttps://www.dataquest.io/blog/basic-statistics-in-python-probability/)

<br>

### What is probability?

<br>

> At the most basic level, probability seeks to answer the question, “What is the chance of an event happening?” An event is some outcome of interest.

> To calculate the chance of an event happening, we also need to consider all the other events that can occur.

- The quintessential representation of probability is the humble coin toss. In a coin toss the only events that can happen are:
  - Flipping a heads
  - Flipping a tails

> These two events form the sample space, the set of all possible events that can happen. 

> To calculate the probability of an event occurring, we count how many times are event of interest can occur (say flipping heads) and dividing it by the sample space.

> Probability will tell us that an ideal coin will have a 1-in-2 chance of being heads or tails.

> By looking at the events that can occur, probability gives us a framework for making predictions about how often events will happen. 

<br>

### From statistics to probability

<br>

> Our data will be generated by flipping a coin 10 times and counting how many times we get heads.

> We will call a set of 10 coin tosses a trial.

> Our data point will be the number of heads we observe.

> We may not get the “ideal” 5 heads, but we won’t worry too much since one trial is only one data point.

> If we perform many, many trials, we expect the average number of heads over all of our trials to approach the 50%.

> The average improves with more trials. 

> As we get more trials, the deviation away from the average decreases. 

> Given enough data, statistics enables us to calculate probabilities using real-world observations. 

> Probability provides the theory, while statistics provides the tools to test that theory using data.

<br>

### The data and the distribution

<br>

> The normal distribution refers to a particularly important phenomenon in the realm of probability and statistics.

> The most important qualities to notice about the normal distribution is its `symmetry` and its `shape`. 

> The normal distribution is a particular distribution of the probability across all of the events.

> The x-axis takes on the values of events we want to know the probability of.

> The y-axis is the probability associated with each event, from 0 to 1.

<br>

> In a probability context, the high point in a normal distribution represents the event with the highest probability of occurring. 

> As you get farther away from this event on either side, the probability drops rapidly, forming that familiar bell-shape.

> The high point in a statistical context actually represents the mean. As in probability, as you get farther from the mean, you rapidly drop off in frequency.

> That is to say, extremely high and low deviations from the mean are present but exceedingly rare.

<br>

> When the two score distributions overlap too much, it’s probably better to assume thy actually come from the same distribution and aren’t different. 

>  On the other extreme with no overlap, it’s safe to assume that the distributions aren’t the same.

> Our trouble lay in the case of some overlap.

> Given that the extreme highs of one distribution may intersect with the extreme lows of another, how can we say if the groups are different?

<br>

### Revisiting the normal

<br>

- Central Limit Theorem

> With more trials, the closer the average of these trials approach the true probability, even if the individual trials themselves are imperfect.

> This idea is a key tenet of the Central Limit Theorem.

> In our coin-tossing example, a single trial of 10 throws produces a single estimate of what probability suggests should happen (5 heads). We call it an estimate because we know that it won’t be perfect (i.e. we won’t get 5 heads every time).

> If we make many estimates, the Central Limit Theorem dictates that the distribution of these estimates will look like a normal distribution.

> The zenith of this distribution will line up with the true value that the estimates should take on.

> In statistics, the peak of the normal distribution lines up with the mean, and that’s exactly what we observed.

> Thus, given multiple “trials” as our data, the Central Limit Theorem suggests that we can hone in on the theoretical ideal given by probability, even when we don’t know the true probability.

> Central Limit Theorem lets us know that the average of many trials means will approach the true mean, the Three Sigma Rule will tell us how much the data will be spread out around this mean.

<br>

- Three Sigma Rule

> The Three Sigma rule, also known as the empirical rule or 68-95-99.7 rule, is an expression of how many of our observations fall within a certain distance of the mean.

> Remember that the standard deviation (a.k.a. “sigma”) is the average distance an observation in the data set is from the mean.

> The Three Sigma rule dictates that given a normal distribution, 68% of your observations will fall between one standard deviation of the mean.

> 95% will fall within two, and 99.7% will fall within three.

> A lot of complicated math goes into the derivation of these values, and as such, is out of the scope of this article.\

> The key takeaway is to know that the Three Sigma Rule enables us to know how much data is contained under different intervals of a normal distribution.

> Three Sigma rule is a statement of how much of your data falls within known values, it is also a statement of the rarity of extreme values.

> Any value that is more than three standard deviations away from the mean should be treated with caution or care.

> By taking advantage of the Three Sigma Rule and the Z-score.

<br>

### Z-score

<br>

> The Z-score is a simple calculation that answers the question, “Given a data point, how many standard deviations is it away from the mean?

> Z-score doesn’t provide much information to you.

> It gains the most value when compared against a Z-table, which tabulates the cumulative probability of a standard normal distribution up until a given Z-score.

> A standard normal is a normal distribution with a mean of 0 and a standard deviation of 1.

> The Z-score lets us reference this the Z-table even if our normal distribution is not standard.

> The cumulative probability is the sum of the probabilities of all values occurring, up until a given point.

<br>

> The mean is the exact middle of the normal distribution, so we know that the sum of all probabilites of getting values from the left side up until the mean is 50%.

> The values from the Three Sigma Rule actually come up if you try to calculate the cumulative probability between standard deviations.

<br>

> Sum of all probabilities must equal 100%, so we can use the Z-table to calculate probabilities on both sides of the Z-score under the normal.

> calculation of probability of being past a certain Z-score is useful to us. It lets us ask go from “how far is a value from the mean” to “how likely is a value this far from the mean to be from the same group of observations?