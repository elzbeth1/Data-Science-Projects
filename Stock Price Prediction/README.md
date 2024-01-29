# Project overview

Lets say we are interested in trading stocks. We have to make profitable stock trade with miniml risk. When we buya stock we have to be fairly certain that the price will increase. We'll create a machine learning algorithm to predict if the stock price will increase tomorrow. If the algorithm says that the price will increase, we'll buy stock. If the algorithm says that the price will go down, we won't do anything.

# Machine Learning Setup

To tell us when to trade, we want to train a machine learning model. This model needs to predict tomorrow's closing price using data from today. If the model says that the price will increase, we'll buy stock. If the model says that the price will go down, we won't do anything.
We want to maximise our true positives. That is the days when model predicts the price goes up and it actually does. Therefore we will use precision as our error metric. 

                                      Precision = True Positives/(True Positives + False Positives)

This will minimise how much money we will lose by false positives. This means that we will have to accept a lot of false negatives - days when we predict that the price will go down, but it actually goes up. This is okay, since we'd rather minimize our potential losses than maximize our potential gains.

So our model will have low recall, but high precision.

# Dataset

I used MSFT stock prices from Yahoo Fonance for this project.

