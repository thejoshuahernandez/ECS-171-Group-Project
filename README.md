# NFL Scoreline Predictions (39% Average ROI???) - Joshua Hernandez, Justin Wallasch

## Introduction

We decided to do our project on NFL score predictions. This is exciting because we can process our data and predict games based off the prevous weeks' scores. Neither of us bet, but this analysis could be useful to make a few extra dollars by predicting good odds and if a game should be close and exciting. The better our predictions are, the more money made and better games watched by someone using them. This would be done by watching the difference between the model prediction, and the spread lines. 
To be honest, it just felt like something fun to do. We both enjoy watching football games, so why not try to build the model that can predict the result before it even happens?

## Preprocessing

In preprocessing, Josh cleaned up a bunch of the data that we didn't need. Some columns, like weather, or type of grass, were deemed as non-necessary. We chose to focus on raw NFL statistics, leaving us with 16 columns that we could use. We then duplicated the columns and populated the data with the opponents statistics for that game.
We chose to use histograms to see distribution analysis of each statistic which turned out pretty exciting and fun. Below is just one of our histograms using score.

![image](https://user-images.githubusercontent.com/97709241/206362477-54fe2aaa-6ea6-4a2c-952d-74d004260290.png)


We then chose to standardize our data because we planned on using a neural network later in our project using MinMaxScaler(). This standardization is important as we must use the same standardization with our inputted test/prediction data, which we will see later.


## Bulding our models (Methods)

Then it was time to build our two models, so we used our data to train and test for our first model. Our models were both variations on a Keras NN, we used a Sequential model for both. The better of the two models were the first, as it had a lower train and test MSE.
```
(Dense(units = 16,activation = 'relu', input_dim= 36))
(Dense(units = 1,activation = 'relu'))
```
Then fit it using batch_size = 1, epochs = 100. Lastly we predicted our model then plotted our first model's results to get a better view of the scope of the predictions.

![Model 1 fixed](https://user-images.githubusercontent.com/97709241/206352506-0e62d7ae-cefd-45dc-a3ee-0a424a9a700c.PNG)

For the second model we used most of the same parameters execpt we added a few more layers.

```
(Dense(units = 16,activation = 'relu', input_dim= 36))
(Dense(units = 16,activation = 'relu'))
(Dense(units = 16,activation = 'relu'))
(Dense(units = 1,activation = 'relu'))
```

which produced the model below

![Model 2 fixed](https://user-images.githubusercontent.com/97709241/206352624-07c8c7d9-c1ed-42f9-b065-437be1973ef6.PNG)

Both of these images show the relationship between the predicted scoress and the actual scores. The model tended to condense the actual score, meaning it never wanted to predict too low, (below ten) or too high (somewhere above 50). This makes sense as scorelines like that are so rare.

Again, we used the first model as the actual model, since our MSE's were lower. 

## Generation of Data for Predicting
Now, we need to find a way to generate the statistics of each team in week 13. There's no way to really determine if a team will be "on fire" and perform better than normal, or "worse than" normal, so we deemed the best possible way to do create our data was to use the last four weeks as an average performance metric. We took each of the four games, summed all their statistics, and took the average as the week 13 prediction data. Then we ran these predicted statistics through the model, with the "opposing" team statistics being the average stats from the team that they were facing that week.

A shortcoming of this model is this use of the "average" to predict the score. Some things happen from week to week, like for instance, in the Ravens game, the Ravens QB went down with an injury, which led to the game being extremely low scoring. If we knew the quarterback would be out, then the passing yards and Tds would be lower than the average, leading to our model predicting lower.

## Results

Finally, we used this generated data to predict week 13 in the NFL! We did this by adding the previous four weeks data into the analysis and predicted each teams' scores. Below are our results, and the model went 11-15 for 73.33%. If we bet on the spreads covering as predicted by our model, we would have made a 40% return on investment!

![image](https://user-images.githubusercontent.com/97709241/206362195-72ab0881-ba68-4c9f-9d89-74c27fe19a4f.png)

![pie chart](https://user-images.githubusercontent.com/97709241/206355137-98f47b88-caa5-4c96-a930-15c1c91b4b17.PNG)




## Discussion

We decided to do our project on NFL scores because it is of common interest to both of us. We went into this project not necessarily thinking we could accurately determine the scores, but are surprised with how accurate our project ended up being. Most of the games we predicted had the predicted outcome as far as who won and who lost. The exact score was more difficult to accurately determine, as we expected, but some of our predictions were surprisingly close. One thing that is lacking from our results is injury list and trade list. I believe if we somehow added weights on traded players and also excluded injurded players from the four weeks of statistics we could get even more accurate score predictions. Also, out of our four upsets, three of them came from home field teams. If we could somehow add which team was away and improve their predicteded score due to their home or away advantages and disadvantages, this would improve our accuracy. Lastly we mentioned beting above and we wanted to see what would happen if we bet on our model. We were shocked to see the ammount of money we would make from week thirteen so we went back another week to week 12 and our graph predicted 13/16 for result and went 11.5/16 on spreads! below is an excel of our findings.

![image](https://user-images.githubusercontent.com/97709241/206362220-08c224a5-a758-45f6-b131-a59a0261f9fc.png)

## Conclusion

Our results were exciting and it was fun to watch the games with our predictions. For a project that two students worked on when there are millions of people trying to predict these scores, I would say we did pretty well. I hope you enjoyed our project and maybe use it to spice up your future game watching. I would like to work on this repo in the future and see if I could add something for home field advantage. This made sports watching really fun. I am also a huge hockey fan so it would also be fun to do a similar project with hockey. I believe the tricky part would be the goalies because they can be switched and each goalie usally have completely different stats than their back ups.

## Contributions

Josh did the coding work, and anything you see in the jupyter notebook. Justin did everything here in the readme.

## Update #1 (Built our Repo, preprocessing, and normalization)

Our dataset, found on this github repo, has been cropped to only include the most important data. Some columns were deemed redundant and non-necessary to have for our network, and were thus cropped out. 

We processed the data by pruning these non-necessary columns, creating columns like score, and pass_yards/att/cmp that we deemed to be the most necessary.

After, we standardized the dataset. More information about our work can be found in the jupyter notebook. Thank you!

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

## Update #3.0 (Completed the write and made our summary easy to follow and read without going into the coding)

