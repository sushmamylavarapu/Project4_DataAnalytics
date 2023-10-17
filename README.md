### part_01_API.ipynb (Team Work)

Use 'TMDB10000.csv' as source file for TMDB movie ID. Crearte TMDB API request by TMDB ID. In the response, extract the By OMDB ID, request OMDB API and complete the data. Final data is a combination of TMDB and OMDB data. Related File:

- original movie list 'TMDB10000.csv'
- required movie info from TMDB API and OMDB API. save as movie_data.json for 5000 lines with odd index
- movie_data_2.json for 5000 lines with even index
- combine movie_data.json and movie_data_2.json as movie_data_big.json

### part_02_data_clean.ipynb (Team Work)

Clean data, save as 'movie_tableau.csv' and 'movie_machine_learning.csv' for later use

### part_03_data_prepare_tableau.ipynb (Sushma Mylavarapu)
https://public.tableau.com/app/profile/sushma6917/viz/TMDB-Movie-Database/Revenue?publish=yes

### part_04_machine_learning_rating.ipynb (Ana Maria Torres)
#### Cleaning the data and dropping columns.
Looking for a model that can predict movie ratings by category. Listing the movies by genre.

#### Analyze whether there was a relationship between voting and years.
The graph shows that in recent years higher ratings are obtained than 100 years ago.

#### Machine Learing: Finding the model that best fits the data

##### Regression Models:
We obtained 3 measurement values:
R2 (Rsqare): Measure to determin the model fit. The closer it is to 1, the better the model fits the data.
MSE (The Mean Sqare Error) and RMSE (Rute Mean Sqare Error): As they are error measurements, we look for values as close to 0.

The Random Forest Regressor although the R2 (R-Sqare) is still low (0.31) is the model that best fits the data.

##### Classifiers:
Pprecision, recall and F1-Score as they are not error reports but accuracy reports, we look for the values to be as close to 1 as possible.
Confusion Matrix method, we look for the diagonal to have the largest numbers and the numbers that are not in the diagonal to be 0 (since these are the errors).

Random Forest Classifier, the model performs better on movies for category 6 (precision of 0.67). 

With an accurancy of 0.60 the Random Forest Classifier is the model that has the best accuracy with respect to the data.

### part_05_machine_learning_genres.ipynb (Jiaolu Xie)

#### Prepare Predictor
  
Combine multiple text content to one text string. Split the string as a list and remove stop words. Create the ‘frequency’ for words, this is the Feature to use.

#### Multi-Class Problem for Genres (Collapse Multi Genres to one Genres)
  
Check the overall frequency for multi genres. Keep all Genres over 200 counts, less than 200 counts are combined to Other. Reclassify label_genre for each movie. Selecting the genre has a lower overall count to represent the ‘uniqueness’ of the movie. 

Use label_genre as Target, Logistic regression model gives Accuracy at 0.379.

Compare the accuracy with educated random guesses.

Conclusion: even though the accuracy is 0.379, for natural language this model still captures some pattern.

#### Multi-Label Problem for Genres
  
Convert genres to multiple binary columns, use multiple columns as Target. Introducing threshold value. Consider genres that have probability > 0.35 or the genre with maximum probability as predicted genre(s). Hence, selecting 1 to 3 genres as a prediction result. Logistic regression model gives f1 score at 0.617.

Implement the trained model to other text, such as book description.

Compare the predicted genres with actual genres.

Conclusion: The accuracy only improved 0.02, after doubling the database from 5000 to 10000. The model not only captures the feature in the predictor but also captures the distribution or probability of the database, with a better selected training set we should be able to get better results.


  

