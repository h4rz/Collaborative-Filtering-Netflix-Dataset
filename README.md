# Collaborative-Filtering-Netflix-Dataset
Empirical Analysis of Predictive Algorithms for Collaborative Filtering

## Problem Statement

- Read the attached paper on Empirical Analysis of Predictive Algorithms for Collaborative Filtering. You need to read up to Section 2.1, and are encouraged to read further if you have time.
- The dataset we will be using is a subset of the movie ratings data from the Netflix Prize. You need to download it via Elearning. It contains a training set, a test set, a movies file, a dataset description file, and a README file. The training and test sets are both subsets of the Netflix training data. You will use the ratings provided in the training set to predict those in the test set. You will compare your predictions with the actual ratings provided in the test set. The evaluation metrics you need to use are the Mean Absolute Error and the Root Mean Squared Error. The dataset description file further describes the dataset, and will help you get started. The README file is from the original set of Netflix files, and has been included to comply with the terms of use for this data.
- Implement (use Python3 and numpy; the latter is a must for this part) the collaborative filtering algorithm described in Section 2.1 of the paper (Equations 1 and 2; ignore Section 2.1.2) for making the predictions.

## Solution

- The task was to implement memory-based collaborative filtering on the Netflix data. In this approach, we predict the votes of a particular user from the database of user votes from a sample or population of other users.
- Firstly, we calculate the mean vote of each user from the training dataset with the help of the below formula –

![equation](http://www.sciweavers.org/upload/Tex2Img_1647480784/render.png)

- To calculate the mean vote of each user, we use Panda’s groupby() on the training set and calculate the sum and count of rating for each user which helps in retrieving the numerator (sum) and denominator (count). The next step is to simply divide the numerator and denominator to get the Vi bar for all the users. 
- The formula for predicting is given by –

![equation](http://www.sciweavers.org/upload/Tex2Img_1647481012/render.png)

- The issue over here is that for predicting for each user we have to calculate the weights for each user overall the users and their votes which is time-consuming. So, for faster implementation, we use sci-kit-learn’s k-neighbors to find the nearest neighbors to user a from the set of users who has voted for movie j.
- There are methods implemented for finding neighbors (get_nearest_users()) and weights (get_correlation()) available in the source code for reference.

- After running the model, we get the below evaluation –
  - **Mean absolute error = 0.8015884074125679**
  - **Root mean square error = 1.0945198425711442**


