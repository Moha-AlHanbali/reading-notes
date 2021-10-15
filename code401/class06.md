[Home](README.md)

<br>

# Game of Greed 1

<br>

## Readings from [How to use the Random Module in Python](https://www.pythonforbeginners.com/random/how-to-use-the-random-module-in-python)

<br>

> The random module provides access to functions that support many operations.

> Perhaps the most important thing is that it allows you to generate random numbers.

<br>

### When to use it?

<br>

> We want the computer to pick a random number in a given range Pick a random element from a list.

> Making a password database more secure or powering a random page feature of a website.

<br>

### Random functions

<br>

- Randint: If we wanted a random integer, we can use the randint function Randint accepts two parameters: a lowest and a highest number.
  - `random.randint(lower, higher)`

- Random: If you want a larger number, you can multiply it.
  - `random.random() * int`

- Choice: Generate a random value from the sequence sequence.
  - `random.choice( ['val1', 'val2', 'val3'] )`

- Shuffle: The shuffle function, shuffles the elements in list in place, so they are in a random order.
  - `shuffle(['val1', 'val2', 'val3'])`

- Randrange: Generate a randomly selected element from range(start, stop, step).
  - `random.randrange(start, stop[, step])`

<br>

## Readings from [What is Risk Analysis in Software Testing and how to perform it?](https://www.edureka.co/blog/risk-analysis-in-software-testing/)

<br>

> The probability of any unwanted incident is defined as Risk.

> In Software Testing, risk analysis is the process of identifying the risks in applications or software that you built and prioritizing them to test.

> After that, the process of assigning the level of risk is done.

> The categorization of the risks takes place, hence, the impact of the risk is calculated.

<br>

### Why use Risk Analysis?

<br>

> Using risk analysis at the beginning of a project highlights the potential problem areas.

> Knowing about the risk areas, it helps the developers and managers to mitigate them.

> When a test plan has been created, risks involved in testing the product are to be taken into consideration along with the possibility of the damage they may cause to your software along with solutions

<br>

### Possible Risks

<br>

- Use of new hardware

- Use of new technology

- Use of new automation tool

- The sequence of code

- Availability of test resources for the application

<br>

### Unavoidable Risks

<br>

- The time that you allocated for testing

- A defect leakage due to the complexity or size of the application

- Urgency from the clients to deliver the project

- Incomplete requirements

<br>

- To tackle the situation with care, follow points can be taken care of:
  - Conduct Risk Assessment review meeting
  - Use maximum resources to work on high-risk areas
  - Create a Risk Assessment database for future use
  - Identify and notice the risk magnitude indicators: high, medium, low.

<br>

### risk magnitude indicators

<br>

- High: means the effect of the risk would be very high and non-tolerable. The company might face loss.

- Medium: it is tolerable but not desirable. The company may suffer financially but there is a limited risk.

- Low: it is tolerable. There lies little or no external exposure or no financial loss.

<br>

### Risk Identification

<br>

- Business Risks: 
  - This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.

- Testing Risks:
  - You should be well acquainted with the platform you are working on, along with the software testing tools being used.

- Premature Release Risk:
  - A fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required.

- Software Risks:
  - You should be well versed with the risks associated with the software development process.

<br>

### Risk Assessment

<br>

> After risk identification, assessment has to be dealt programmatically. There are a few perspectives on risk assessment.

1. Early Forecast of unwanted situation in project
2. Estimating potential loss of such situations
3. Making decisions to deal with such situations
4. Avoid future consequences

<br>

### The perspective of Risk Assessment

<br>

- Effect 
  - To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.

- Cause 
  - To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.

-  Likelihood 
  - To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.

<br>

### How to perform Risk Analysis?

<br>

1. Searching the risk
2. Analyzing the impact of each individual risk
3. Measures for the risk identified

<br>

## Readings from [Test Coverage (Code Coverage)](https://martinfowler.com/bliki/TestCoverage.html)

<br>

> Test coverage is a useful tool for finding untested parts of a codebase. Test coverage is of little use as a numeric statement of how good your tests are.

<br>

> High coverage numbers are too easy to reach with low quality testing. At the most absurd level you have AssertionFreeTesting.

> You get lots of tests looking for things that rarely go wrong distracting you from testing the things that really matter.

> TDD is a very useful, but certainly not sufficient, tool to help you get good tests.

> If you are testing thoughtfully and well, I would expect a coverage percentage in the upper 80s or 90s. I would be suspicious of anything like 100%

> Why people focus on coverage numbers is because they want to know if they are testing enough.

> Low coverage numbers, say below half, are a sign of trouble.

> But high numbers don't necessarily mean much, and lead to ignorance-promoting dashboards.

> Sufficiency of testing is much more complicated attribute than coverage can answer.

<br>

- You are doing enough testing if the following is true:
  - You rarely get bugs that escape into production.
  - You are rarely hesitant to change some code for fear it will cause production bugs.

<br>

- Signs that you are testing too much:
  - If you can remove tests while still having enough.
  - If your tests are slowing you down.
  - If it seems like a simple change to code causes excessively long changes to tests.
    - This may not be so much that you are testing too many things, but that you have duplication in your tests.

<br>

> Some people think that you have too many tests if they take too long to run. 

> You can always move slow tests to a later stage in your deployment pipeline, or even pull them out of the pipeline and run them periodically.

> Doing these things will slow down the feedback from those tests, but that's part of the trade-off of build times versus test confidence

<br>

### Value of Test Coverage

<br>

> It helps you find which bits of your code aren't being tested.

> It's worth running coverage tools every so often and looking at these bits of untested code.
