# ECS 171 Group Project - Joshua Hernandez, Justin Wallasch

Our dataset, found on this github repo, has been cropped to only have the most important data. Some columns were deemed redundant and non-necessary to have for our network.

Preprocessing the data was pruning these non-necessary columns, creating columns like score, and pass_yards/att/cmp that we deemed to be the most necessary.

We then normalized the dataset after. More information about our work can be found in the jupyter notebook. Thank you!

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
