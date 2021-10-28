[Home](README.md)

<br>

# Machine Learning Intro

<br>

## Readings from [Data Science Primer](https://elitedatascience.com/primer)

<br>

### Chapter 1: Bird's Eye View

<br>

- Generally speaking, we can break down applied machine learning into the following chunks
  - Exploratory Analysis
  - Data Cleaning
  - Feature Engineering
  - Algorithm Selection
  - Model Training
  - Other

<br>

#### Machine Learning ≠ Algorithms

<br>

> Machine learning is not about algorithms.

> Machine learning is a comprehensive approach to solving problems...

<br>

#### What makes machine learning so special?

<br>

> Machine learning is the practice of teaching computers how to learn patterns from data, often for making decisions or predictions.

> For true machine learning, the computer must be able to learn patterns that it's not explicitly programmed to identify.

> It's only machine learning because what is learned is the learned patterns.

<br>

#### Key Terminology

<br>

> `Model` - a set of patterns learned from data.

> `Algorithm` - a specific ML process used to train a model.

> `Training data` - the dataset from which the algorithm learns the model.

> `Test data` - a new dataset for reliably evaluating model performance.

> `Features` - Variables (columns) in the dataset used to train the model.

> `Target variable` - A specific variable you're trying to predict.

> `Observations` - Data points (rows) in the dataset.

<br>

#### Machine Learning Tasks

<br>

> In applied machine learning, you should first pick the right machine learning task for the job.

> A task is a specific objective for your algorithms.

> Algorithms can be swapped in and out, as long as you pick the right task.

> In fact, you should always try multiple algorithms because you most likely won't know which one will perform best for your dataset.

> The two most common categories of tasks are supervised learning and unsupervised learning.

> `Supervised learning` includes tasks for "labeled" data (i.e. you have a target variable).

> `Unsupervised learning` includes tasks for "unlabeled" data (i.e. you do not have a target variable).

<br>

- Supervised Learning
  - In practice, it's often used as an advanced form of predictive modeling.
  - Each observation must be labeled with a "correct answer."
  - Only then can you build a predictive model because you must tell the algorithm what's "correct" while training it (hence, "supervising" it).
  - Regression is the task for modeling continuous target variables.
  - Classification is the task for modeling categorical (a.k.a. "class") target variables.

<br>

- Unsupervised Learning
  - In practice, it's often used either as a form of automated data analysis or automated signal extraction.
  - Unlabeled data has no predetermined "correct answer."
  - You'll allow the algorithm to directly learn patterns from the data (without "supervision").
  - Clustering is the most common unsupervised learning task, and it's for finding groups within your data.

<br>

#### The 3 Elements of Great Machine Learning

<br>

- A skilled chef (human guidance)
  - First, even though we are "teaching computers to learn on their own," human guidance plays a huge role.
  - As you'll see, you'll need to make dozens of decisions along the way.
  - In fact, the very first major decision is how to road-map your project for guaranteed success.

- Fresh ingredients (clean, relevant data)
  - The second essential element is the quality of your data.
  - Garbage In = Garbage Out, no matter which algorithms you use.
  - Professional data scientists spend most their time understanding the data, cleaning it, and engineering new features.
  - While that sounds open-ended, you'll get our proven frameworks that you can always rely on as starting points.

- Don't overcook it (avoid overfitting)
  - One of the most dangerous pitfalls in machine learning is overfitting. An overfit model has "memorized" the noise in the training set, instead of learning the true underlying patterns.
  - An overfit model within a hedge fund can cost millions of dollars in losses.
  - An overfit model within a hospital can costs thousands of lives.
  - For most applications, the stakes won't be quite that high, but overfitting is still the single largest mistake you must avoid.

<br>

#### The Blueprint

<br>

> Machine learning blueprint is designed around these elements.

- The are 5 core steps:
  - `Exploratory Analysis` First, "get to know" the data. This step should be quick, efficient, and decisive.
  - `Data Cleaning` Then, clean your data to avoid many common pitfalls. Better data beats fancier algorithms.
  - `Feature Engineering` Next, help your algorithms "focus" on what's important by creating new features.
  - `Algorithm Selection` Choose the best, most appropriate algorithms without wasting your time.
  - `Model Training` Finally, train your models. This step is pretty formulaic once you've done the first 4.

- Other situational steps:
  - `Project Scoping` Sometimes, you'll need to roadmap the project and anticipate data needs.
  - `Data Wrangling` You may also need to restructure your dataset into a format that algorithms can handle.
  - `Preprocessing` Often, transforming your features first can further improve performance.
  - `Ensembling` You can squeeze out even more performance by combining multiple models.

<br>

### Chapter 2: Exploratory Analysis

<br>

> There’s a big challenge in data science called “Tactical Hell.” This is actually a term from startups, and it’s when you have too many tactics to choose from:

> Should you develop your product more? Invest in marketing? Hire an accountant? Etc.

> In many ways, training a ML model is like growing a startup. You also have too many tactics to choose from:

> Should you clean your data more? Engineer features? Test new algorithms? Etc.

> There’s a lot of trial and error, so how do you avoid chasing dead ends? The answer is “Exploratory Analysis.” (Which is just fancy-talk for “getting to know” your data.)

> Doing this upfront helps you save time and avoid wild goose chases… As a data scientist, you are a commander with limited resources (i.e. time). Exploratory analysis is like sending scouts to learn where to deploy your forces!

<br>

#### Why explore your dataset upfront?

<br>

> The purpose of exploratory analysis is to "get to know" the dataset. 

- Doing so upfront will make the rest of the project much smoother, in 3 main ways:
  - You’ll gain valuable hints for Data Cleaning (which can make or break your models).
  - You’ll think of ideas for Feature Engineering (which can take your models from good to great).
  - You’ll get a "feel" for the dataset, which will help you communicate results and deliver greater impact.

> However, exploratory analysis for machine learning should be quick, efficient, and decisive... not long and drawn out!

> Don’t skip this step, but don’t get stuck on it either.

> You see, there are infinite possible plots, charts, and tables, but you only need a handful to "get to know" the data well enough to work with it.

<br>

#### Start with Basics

<br>

- First, you'll want to answer a set of basic questions about the dataset:
  - How many observations do I have?
  - How many features?
  - What are the data types of my features? Are they numeric? Categorical?
  - Do I have a target variable?

<br>

#### Plot Numerical Distributions

<br>

> Often, a quick and dirty grid of histograms is enough to understand the distributions.

- Here are a few things to look out for:
  - Distributions that are unexpected
  - Potential outliers that don't make sense
  - Features that should be binary (i.e. "wannabe indicator variables")
  - Boundaries that don't make sense
  - Potential measurement errors

> At this point, you should start making notes about potential fixes you'd like to make.

> If something looks out of place, such as a potential outlier in one of your features, now's a good time to ask the client/key stakeholder, or to dig a bit deeper.

<br>

#### Plot Categorical Distributions

<br>

> Categorical features cannot be visualized through histograms. Instead, you can use bar plots.

> In particular, you'll want to look out for sparse classes, which are classes that have a very small number of observations.

> By the way, a "class" is simply a unique value for a categorical feature.

- Sparse classes tend to be problematic when building models.
  - In the best case, they don't influence the model much.
  - In the worse case, they can cause the model to be overfit.

<br>

#### Plot Segmentations

<br>

> Segmentations are powerful ways to observe the relationship between categorical features and numeric features.

> Box plots allow you to do so.

<br>

#### Study Correlations

<br>

> Finally, correlations allow you to look at the relationships between numeric features and other numeric features.

> Correlation is a value between -1 and 1 that represents how closely two features move in unison.

> You don't need to remember the math to calculate them.

- Just know the following intuition:
  - `Positive correlation` means that as one feature increases, the other increases. E.g. a child’s age and her height.
  - `Negative correlation `means that as one feature increases, the other decreases. E.g. hours spent studying and number of parties attended.
  - `Correlations near -1 or 1` indicate a strong relationship.
  - `Those closer to 0` indicate a weak relationship.
  - `0` indicates no relationship.

> Correlation heatmaps help you visualize this information.

- In general, you should look out for:
  - Which features are strongly correlated with the target variable?
  - Are there interesting or unexpected strong correlations between other features?

> By the end of your Exploratory Analysis step, you'll have a pretty good understanding of the dataset, some notes for data cleaning, and possibly some ideas for feature engineering.

<br>

### Chapter 3: Data Cleaning

<br>

> Proper data cleaning is the “secret” sauce behind machine learning… Well, it’s not really a “secret”… It’s just a bit boring, so no one really talks about it.

> But the truth is: Better data beats fancier algorithms…

> Garbage in = Garbage out... Plain and Simple! If you have a clean dataset, even simple algorithms can learn impressive insights from it!

<br>

#### Better Data > Fancier Algorithms

<br>

> Data cleaning is one those things that everyone does but no one really talks about. Sure, it’s not the most attractive part of machine learning. And no, there aren’t hidden tricks and secrets to uncover.

> However, proper data cleaning can make or break your project. Professional data scientists usually spend a very large portion of their time on this step.

> `Better data beats fancier algorithms.`

> In fact, if you have a properly cleaned dataset, even simple algorithms can learn impressive insights from the data!

> Obviously, different types of data will require different types of cleaning. However, the systematic approach laid out in this lesson can always serve as a good starting point.

<br>

#### Remove Unwanted observations

<br>

> This includes duplicate or irrelevant observations.

- Duplicate observations
  - Combine datasets from multiple places
  - Scrape data
  - Receive data from clients/other departments

- Irrelevant observations
  - For example, if you were building a model for Single-Family homes only, you wouldn't want observations for Apartments in there.
  - This is also a great time to review your charts from Exploratory Analysis. You can look at the distribution charts for categorical features to see if there are any classes that shouldn’t be there.
  - Checking for irrelevant observations before engineering features can save you many headaches down the road.

<br>

#### Fix Structural Errors

<br>

> The next bucket under data cleaning involves fixing structural errors.

> Structural errors are those that arise during measurement, data transfer, or other types of "poor housekeeping."

> For instance, you can check for typos or inconsistent capitalization. This is mostly a concern for categorical features, and you can look at your bar plots to check.

> Finally, check for mislabeled classes, i.e. separate classes that should really be the same.

<br>

#### Filter Unwanted Outliers

<br>

> Outliers can cause problems with certain types of models. For example, linear regression models are less robust to outliers than decision tree models.

> In general, if you have a legitimate reason to remove an outlier, it will help your model’s performance.

> However, outliers are innocent until proven guilty. You should never remove an outlier just because it’s a "big number." That big number could be very informative for your model.

> We can’t stress this enough: you must have a good reason for removing an outlier, such as suspicious measurements that are unlikely to be real data.

<br>

#### Handle Missing Data

<br>

> First, just to be clear, you cannot simply ignore missing values in your dataset.

> You must handle them in some way for the very practical reason that most algorithms do not accept missing values.

> `"Common sense" is not sensible here.`

- Unfortunately, the 2 most commonly recommended ways of dealing with missing data actually suck.
  - `Dropping observations` that have missing values
    - Dropping missing values is sub-optimal because when you drop observations, you drop information.
    - The fact that the value was missing may be informative in itself.
    - Plus, in the real world, you often need to make predictions on new data even if some of the features are missing!
  - `Imputing the missing values` based on other observations
    - Imputing missing values is sub-optimal because the value was originally missing but you filled it in, which always leads to a loss in information, no matter how sophisticated your imputation method is.
    - Again, "missingness" is almost always informative in itself, and you should tell your algorithm if a value was missing.
    - Even if you build a model to impute your values, you’re not adding any real information. You’re just reinforcing the patterns already provided by other features.

> In short, `you should always tell your algorithm that a value was missing because missingness is informative`.

<br>

- Missing categorical data
  - The best way to handle missing data for categorical features is to simply label them as ’Missing’!
  - You’re essentially adding a new class for the feature.
  - This tells the algorithm that the value was missing.
  - This also gets around the technical requirement for no missing values.

- Missing numeric data
  - For missing numeric data, you should flag and fill the values.
  - Flag the observation with an indicator variable of missingness.
  - Then, fill the original missing value with 0 just to meet the technical requirement of no missing values.
  - By using this technique of flagging and filling, you are essentially allowing the algorithm to estimate the optimal constant for missingness, instead of just filling it in with the mean.

<br>

#### Chapter 4: Feature Engineering

<br>

> In a nutshell, “feature engineering” is creating new model input features from your existing ones.

> ‘Applied machine learning’ is basically feature engineering.”

> To start, feature engineering is very open-ended. There are literally infinite options for new features to create. Plus, you’ll need domain knowledge to add informative features instead of more noise.

<br>

#### What is Feature Engineering?

<br>

> In general, you can think of data cleaning as a process of subtraction and feature engineering as a process of addition.

- This is often one of the most valuable tasks a data scientist can do to improve model performance, for 3 big reasons:
  - You can isolate and highlight key information, which helps your algorithms "focus" on what’s important.
  - You can bring in your own domain expertise.
  - Most importantly, once you understand the "vocabulary" of feature engineering, you can bring in other people’s domain expertise!

<br>

#### Infuse Domain Knowledge

<br>

> You can often engineer informative features by tapping into your (or others’) expertise about the domain.

> Try to think of specific information you might want to isolate. Here, you have a lot of "creative freedom."

<br>

#### Create Interaction Features

<br>

> The first of these heuristics is checking to see if you can create any interaction features that make sense. These are combinations of two or more features.

> > By the way, in some contexts, "interaction terms" must be products between two variables. In our context, interaction features can be products, sums, or differences between two features.

> A general tip is to look at each pair of features and ask yourself, "could I combine this information in any way that might be even more useful?"

<br>

#### Combine Sparse Classes

<br>

> `Sparse classes` (in categorical features) are those that have very few total observations. They can be problematic for certain machine learning algorithms, causing models to be overfit.

> There's no formal rule of how many each class needs.

> It also depends on the size of your dataset and the number of other features you have.

> As a rule of thumb, we recommend combining classes until each one has at least ~50 observations. As with any "rule" of thumb, use this as a guideline (not actually as a rule).

> Often, an eyeball test is enough to decide if you want to group certain classes together.

<br>

#### Add Dummy Variables

<br>

> Most machine learning algorithms cannot directly handle categorical features. Specifically, they cannot handle text values.

> Therefore, we need to create dummy variables for our categorical features.

> Dummy variables are a set of binary (0 or 1) variables that each represent a single class from a categorical feature.

> The information you represent is exactly the same, but this numeric representation allows you to pass the technical requirements for algorithms.

<br>

#### Remove Unused Features

<br>

- Unused features are those that don’t make sense to pass into our machine learning algorithms. Examples include:
  - ID columns
  - Features that wouldn't be available at the time of prediction
  - Other text descriptions

> Redundant features would typically be those that have been replaced by other features that you’ve added during feature engineering.

> After completing Data Cleaning and Feature Engineering, you'll have transformed your raw dataset into an analytical base table (`ABT`).

> We call it an "`ABT`" because it's what you'll be building your models on.

> Not all of the features you engineer need to be winners. In fact, you’ll often find that many of them don’t improve your model. That’s fine because one highly predictive feature makes up for 10 duds.

> The key is choosing machine learning algorithms that can automatically select the best features among many options (built-in feature selection).

> This will allow you to avoid overfitting your model despite providing many input features.

<br>

### Chapter 5: Algorithm Selection

<br>

> In applied machine learning, individual algorithms should be swapped in and out depending on which performs best for the problem and the dataset.

> Therefore, we will focus on intuition and practical benefits over math and theory.

<br>

#### How to Pick ML Algorithms

<br>

> In applied machine learning, individual algorithms should be swapped in and out depending on which performs best for the problem and the dataset. Therefore, we will focus on intuition and practical benefits over math and theory.

<br>

#### Why Linear Regression is Flawed

<br>

> Simple linear regression models fit a "straight line" (technically a hyperplane depending on the number of features, but it's the same idea).

> In practice, they rarely perform well. We actually recommend skipping them for most machine learning problems.

> Their main advantage is that they are easy to interpret and understand. However, our goal is not to study the data and write a research report.

> Our goal is to build a model that can make accurate predictions.

- In this regard, simple linear regression suffers from two major flaws:
  - It's prone to overfit with many input features.
  - It cannot easily express non-linear relationships.

<br>

#### Regularization in Machine Learning

<br>

> This is the first "advanced" tactic for improving model performance. It’s considered pretty "advanced" in many ML courses, but it’s really pretty easy to understand and implement.

> The first flaw of linear models is that they are prone to be overfit with many input features.

<br>

#### Regularized Regression Algos

<br>

- There are 3 common types of regularized linear regression algorithms.
  - Lasso Regression
    - `Lasso`, or LASSO, stands for `Least` `Absolute` `Shrinkage` and `Selection` `Operator`.
    - Lasso regression penalizes the absolute size of coefficients.
    - Practically, this leads to coefficients that can be exactly 0.
    - Thus, Lasso offers automatic feature selection because it can completely remove some features.
    - Remember, the "strength" of the penalty should be tuned.
    - A stronger penalty leads to more coefficients pushed to zero.
  - Ridge Regression
    - `Ridge` stands Really Intense Dangerous Ridge.
    - Ridge regression penalizes the squared size of coefficients.
    - Practically, this leads to smaller coefficients, but it doesn't force them to 0.
    - In other words, Ridge offers feature shrinkage.
    - Again, the "strength" of the penalty should be tuned.
    - A stronger penalty leads to coefficients pushed closer to zero.
  - Elastic-Net
    - `Elastic-Net` is a compromise between Lasso and Ridge.
    - Elastic-Net penalizes a mix of both absolute and squared size.
    - The ratio of the two penalty types should be tuned.
    - The overall strength should also be tuned.

> There’s no "best" type of penalty. It really depends on the dataset and the problem.

<br>

#### Decision Tree Algos

<br>

- Awesome, we’ve just seen 3 algorithms that can protect linear regression from overfitting. But if you remember, linear regression suffers from two main flaws:
  - It's prone to overfit with many input features.
  - It cannot easily express non-linear relationships.

> Decision trees model data as a "tree" of hierarchical branches. They make branches until they reach "leaves" that represent predictions.

> Due to their branching structure, decision trees can easily model nonlinear relationships.

> Unfortunately, decision trees suffer from a major flaw as well.

> If you allow them to grow limitlessly, they can completely "memorize" the training data, just from creating more and more and more branches.

> As a result, individual unconstrained decision trees are very prone to being overfit.​

<br>

#### Tree Ensembles

<br>

> Ensembles are machine learning methods for combining predictions from multiple separate models. There are a few different methods for ensembling, but the two most common are:

- Bagging
  - `Bagging` attempts to reduce the chance overfitting complex models.
  - It trains a large number of "strong" learners in parallel.
  - A strong learner is a model that's relatively unconstrained.
  - Bagging then combines all the strong learners together in order to "smooth out" their predictions.
- Boosting
  - `Boosting` attempts to improve the predictive flexibility of simple models.
  - It trains a large number of "weak" learners in sequence.
  - A weak learner is a constrained model (i.e. you could limit the max depth of each decision tree).
  - Each one in the sequence focuses on learning from the mistakes of the one before it.
  - Boosting then combines all the weak learners into a single strong learner.

> While bagging and boosting are both ensemble methods, they approach the problem from opposite directions.

> Bagging uses complex base models and tries to "smooth out" their predictions, while boosting uses simple base models and tries to "boost" their aggregate complexity.

> Ensembling is a general term, but when the base models are decision trees, they have special names: random forests and boosted trees!

- Random forests
  - `Random forests` train a large number of "strong" decision trees and combine their predictions through bagging.
  - Each tree is only allowed to choose from a random subset of features to split on (leading to feature selection).
  - Each tree is only trained on a random subset of observations (a process called resampling).
  - Random forests tend to perform very well right out of the box.
    - They often beat many other models that take up to weeks to develop.
    - They are the perfect "swiss-army-knife" algorithm that almost always gets good results.
    - They don’t have many complicated parameters to tune.
- Boosted trees
  - `Boosted trees` train a sequence of "weak", constrained decision trees and combine their predictions through boosting.
  - Each tree is allowed a maximum depth, which should be tuned.
  - Each tree in the sequence tries to correct the prediction errors of the one before it.
  - In practice, boosted trees tend to have the highest performance ceilings.
    - They often beat many other types of models after proper tuning.
    - They are more complicated to tune than random forests.

<br>

### Chapter 6: Model Training

<br>

#### How to Train ML Models

<br>

- Pprofessional data scientists actually spend the bulk of their time on the steps leading up to this one:
  - Exploring the data.
  - Cleaning the data.
  - Engineering new features.

<br>

#### Split Dataset

<br>

- Think of your data as a limited resource.
  - You can spend some of it to train your model (i.e. feed it to the algorithm).
  - You can spend some of it to evaluate (test) your model.
  - But you can’t reuse the same data for both!

> If you evaluate your model on the same data you used to train it, your model could be very overfit and you wouldn’t even know! A model should be judged on its ability to predict new, unseen data.

> Therefore, you should have separate training and test subsets of your dataset.

> You should always split your data before doing anything else.

> This is the best way to get reliable estimates of your models’ performance.

> After splitting your data, don’t touch your test set until you’re ready to choose your final model!

> Comparing test vs. training performance allows us to avoid overfitting... If the model performs very well on the training data but poorly on the test data, then it’s overfit.

<br>

#### What are Hyperparameters?

<br>

> When we talk of tuning models, we specifically mean tuning hyperparameters.

> There are two types of parameters in machine learning algorithms.

> The key distinction is that model parameters can be learned directly from the training data while hyperparameters cannot.

- Model parameters
  - `Model parameters` are learned attributes that define individual models.
  - e.g. regression coefficients
  - e.g. decision tree split locations
  - They can be learned directly from the training data
- Hyperparameters
  - `Hyperparameters` express "higher-level" structural settings for algorithms.
  - e.g. strength of the penalty used in regularized regression
  - e.g. the number of trees to include in a random forest
  - They are decided before fitting the model because they can't be learned from the data

<br>

#### What is Cross-Validation?

<br>

> Cross-validation is a method for getting a reliable estimate of model performance using only your training data.

> There are several ways to cross-validate. The most common one, 10-fold cross-validation, breaks your training data into 10 equal parts (a.k.a. folds), essentially creating 10 miniature train/test splits.

- These are the steps for 10-fold cross-validation:
  - Split your data into 10 equal parts, or "folds".
  - Train your model on 9 folds (e.g. the first 9 folds).
  - Evaluate it on the 1 remaining "hold-out" fold.
  - Perform steps (2) and (3) 10 times, each time holding out a different fold.
  - Average the performance across all 10 hold-out folds.

> The average performance across the 10 hold-out folds is your final performance estimate, also called your cross-validated score. Because you created 10 mini train/test splits, this score is usually pretty reliable.

<br>

#### Fit and Tune Models

<br>

> Basically, all we need to do is perform the entire cross-validation loop detailed above on each set of hyperparameter values we'd like to try.

- The high-level pseudo-code looks like this:

```
For each algorithm (i.e. regularized regression, random forest, etc.):
  For each set of hyperparameter values to try:
    Perform cross-validation using the training set.
    Calculate cross-validated score.
```

<br>

> At the end of this process, you will have a cross-validated score for each set of hyperparameter values... for each algorithm.

> Then, we'll pick the best set of hyperparameters within each algorithm.

```
For each algorithm:
  Keep the set of hyperparameter values with best cross-validated score.
  Re-train the algorithm on the entire training set (without cross-validation).
```
<br>

#### Select Winning Model


<br>

> By now, you'll have 1 "best" model for each algorithm that has been tuned through cross-validation. Most importantly, you've only used the training data so far.

> Because you've saved your test set as a truly unseen dataset, you can now use it get a reliable estimate of each models' performance.

- There are a variety of performance metrics you could choose from. We won't spend too much time on them here, but in general:
  - For regression tasks, we recommend Mean Squared Error (MSE) or Mean Absolute Error (MAE). (Lower values are better)
  - For classification tasks, we recommend Area Under ROC Curve (AUROC). (Higher values are better)

- The process is very straightforward:
  - For each of your models, make predictions on your test set.
  - Calculate performance metrics using those predictions and the "ground truth" target variable from the test set.

- Finally, use these questions to help you pick the winning model:
  - Which model had the best performance on the test set? (`performance`)
  - Does it perform well across various performance metrics? (`robustness`)
  - Did it also have (one of) the best cross-validated scores from the training set? (`consistency`)
  - Does it solve the original business problem? (`win condition`)
