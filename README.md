Using Machine Learning to Find Exoplanets with NASA's Dataset
Ismael Araujo

Link to the article: https://ismaeltrevi.medium.com/using-machine-learning-to-find-exoplanets-with-nasas-dataset-bb818515e3b3


A few weeks ago, I wrote an article about using data science for meaningful data sets and could help the world become a better place. Now, let’s talk a little bit about other worlds. We can train machines to identify candidates for exoplanets with real datasets provided by NASA and Caltech. How cool is that? Thus, I decided to go on an adventure through the mysteries of the universe. My idea is to create a machine learning model that can predict if an observation is a real candidate for an exoplanet or not. The data was collected by the Kepler mission that revealed thousands of planets out of our Solar System. Unfortunately, the Kepler mission ended in 2018, but it gave us thousands of observations, so we can train our machines to find planets as well.

And how did the Kepler telescope find planets so far from us if they can take a clear picture of Pluto from Earth? Well, it was able to find planets by looking for small dips in the brightness of a star when a planet transits in front of it. It is possible to measure the size of the planet based on the depth of the transit and the star’s size.


For this article, I downloaded the most recent dataset from the Caltech website. However, if you feel adventurous, you can use NASA’s API and do some web scraping out of the fountain. I know I want to explore that soon, but for now, let’s keep things a little easier and use NASA’s and Caltech datasets. You can find a similar dataset on Kaggle. However, the dataset was uploaded three years ago and should not be updated. The best prediction on Kaggle got a 95% accuracy. To make things more straightforward, I will skip a few exploratory data analyses, but I shared the notebook’s complete version on my Github. You should have some Python and its main packages prior knowledge to run the following code. However, if you don’t know, you should be able to reproduce the same results running the notebook in full.
First things first, let’s import some packages and print the dataset’s shape and a data frame of it. If you want to know more about the packages imported, they contain very resourceful documentation where you can learn more about them.

We have 9,564 observations and 49 features. The features have some very technical names. Thus, I renamed the columns for more meaningful names. This is an optional step, and you do not need to do it. Since it’s an extended code, you can get it in full on my Github.
Now, let’s understand what data we have. We can take a look at the DataFrame and use .info() method. I identify a few categorical features that we will take care of soon.
Image for post
Let’s choose the targets we want to predict: Exoplanet Archive Disposition and Disposition Using Kepler Data. Since we are focusing on data collected by the Kepler mission, let’s use our second option. We also need a continuous target. Let’s transform our target into a binary feature using lambda.

Cool. We have multiple categorical columns we won’t need for this model. Let’s drop them as well. I would not drop rows with null values in other circumstances, but since we have a dataset with a decent size, let’s drop all the rows with null values. This is the right time to assign our features and target variables.

This dataset contains infinite values. We can fix that with the code below. Don’t worry too much about it. I also added an evaluation function so that we can make our final cell cleaner. This function is optional, and run individual evaluation metrics should return the same results.

Now, let’s run our model. First, we should create a train and test dataset using Sklearn. We will assign 60% of the dataset to the train set and 40% to the test set.

And here is where all the fun happens. We will now run our algorithm. Since we are trying to classify if we have a possible exoplanet or not, we will use a Random Forest Classifier for this model. We will use 100 estimators and the Gini Impurity metric. We will analyze a few metrics for this model, but our main focus is Accuracy. We will also look at Recall, F1 Score, Precision, and Confusion Matrix because it doesn’t hurt. I will add the code and a screenshot of my notebook below. Let’s see what results we get.

Wow, that’s quite impressive. We were able to predict with 96% accuracy rather, or observations is an exoplanet or not. For a model that is quite simple and quick to set up (for you. I took hours), we were able to accomplish a lot. Now you can occasionally let your friends know that you worked on a project with a dataset provided by NASA that could find exoplanets — details aren’t necessary. I ran other models just for fun, and you can see it in my Github repository if you want to try tuning their hyperparameters.
Apparently, we can all try to find a few new worlds out there. Look at us!