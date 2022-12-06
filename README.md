# ECS 171 Group Project - Joshua Hernandez, Justin Wallasch

## Introduction

Joshua and I decided to do our project on NFL score predictions. This is exciting beacause we can process our data and predict games based off the prevous weeks' scores. Neither of us bet, but this analysis could be useful to make a few extra dollars by predicting good odds and if a game should be close and exciting. The better our predictions are, the more money made and better games watched by someone using them. This would be done by watching the difference between the model prediction, and the spread lines. 

## Preprocessing

In preprocessing, Josh cleaned up a bunch of the data that we didn't need. Some columns, like weather, or type of grass, were deemed as non-necessary. We chose to focus on raw NFL statistics, leaving us with 16 columns that we could use.
First we checked the inputed data. For this, the data was defined as each teams' statistics from previous games. We chose to use histograms to see distribution analysis of each statistic which turned out pretty exciting and fun. Below is just one of our histograms using passing yards.

![passing yards histogram](https://user-images.githubusercontent.com/97709241/205541464-c6ad0457-968c-4538-987c-c57e6f634937.PNG)

We then chose to standardize our data because we planned on using a neural network later in our project using MinMaxScaler()

## Bulding our models

Then it was time to build our two models, so we used our data to train and test for our first model. Secondly, we used a Sequential model 

(Dense(units = 16,activation = 'relu', input_dim= 36))

(Dense(units = 1,activation = 'relu'))

Then fit it using batch_size = 1, epochs = 100. Lastly we predicted our model then plotted our first model model.

![Group project model 1](https://user-images.githubusercontent.com/97709241/205544126-f3c09bba-3005-436c-80bc-065a5a6386eb.PNG)

For the second model we used most of the same perameters execpt we changed 

(Dense(units = 16,activation = 'relu', input_dim= 36))

(Dense(units = 16,activation = 'relu'))

(Dense(units = 16,activation = 'relu'))

(Dense(units = 1,activation = 'relu'))

which produced the model below

![Group project model 2](https://user-images.githubusercontent.com/97709241/205546418-ac8bd87f-0c15-40b0-a3ce-f69eee8cd8f5.PNG)

Both of these images show the relationship between the predicted scoress and the actual scores. The model tended to condense the actual score, meaning it never wanted to predict too low, (below ten) or too high (somewhere above 50). This makes sense as scorelines like that are so rare.

We used the first model as the actual model, since our MSE's were lower. 

## Results

Finally, we predicted week 13 in the NFL! We did this by adding the previous four weeks data into the analysis and predicted each teams' scores. Below are our results

![Win loss excel](https://user-images.githubusercontent.com/97709241/205548175-26666e82-3d43-4509-a1dd-dd978e041719.PNG)

## Finish

Our results were exciting and it was fun to watch the games with our predictions. One thing that is lacking from our results is injury list, trade list, and home field advantage. Out of our four upsets, three of them came from home field teams. For a project that two students worked on when there are millions of people trying to predict these scores, I would say we did pretty well. I hope you enjoyed our project and maybe use it to spice up your future game watching. 

## Update #1 (Built our Repo, preprocessing, and normalization)

Our dataset, found on this github repo, has been cropped to only include the most important data. Some columns were deemed redundant and non-necessary to have for our network, and were thus cropped out. 

We processed the data by pruning these non-necessary columns, creating columns like score, and pass_yards/att/cmp that we deemed to be the most necessary.

After, we normalized the dataset. More information about our work can be found in the jupyter notebook. Thank you!

## Update #2 (Preprocessing and First Model Building, 11/27) 

ALL UPDATES ARE INSIDE THE JUPYTER NOTEBOOK

-Changed Dataframe to add opposition statistics as extra columns

-Added new "fumbles lost" column

-Cleaned up any NA's in the data

-Successfully built first model!

### -Josh here, giving a few comments:

-Prof/TA, I would love to tell you where our model falls on the fitting graph. (Under/over fitted, good fit, etc.) But in our case, our testing MSE was actually lower than our training MSE. I am unsure of why this is. Maybe you could provide us with some insight on why this is possible? 

-My insight is I think it might be because the training had more "HARD" cases while the test set had more "Easy" set. What I mean is, that when we take a look at the graph I generated on ytest vs yhat, they tend to differ more when ytest is higher. This makes sense, as the model wants to predict a lower score, since high scores are so uncommon. I would say that our unsure fit is due to the test case having less of these "high score games" leading to less error. 

-I plan to look this up in more detail on the second run. I could possibly remove outliers from the data set and run it again, but I prefered to keep as is and provide this analysis with our first run instead of fabricating a second run.

## Update #2.1 (Cleaned up text and made things easier to read 11/27)
