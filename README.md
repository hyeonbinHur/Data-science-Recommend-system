# Data-science-Recommend-system

## Content
  - [Overview](#overview)
  - [Dataser](#dataset)
  - [User based collaborative filltering](#user-based-collaborative-filltering)
  - [Item based collaborative filltering](#item-based-collaborative-filltering)
  - [My recommendation system](#my-recommendation-system)
  
## Overview

This project aims to provide basic and comprehensive knowledge about recommendation systems. While there are multiple ways to create recommendation systems, this project focuses on three different types. In the first task, a user-based collaborative filtering system is implemented, and in the second task, an item-based collaborative filtering system is created. Finally, I have implemented my own collaborative filtering system, utilizing both user-based and item-based collaborative filtering. 

## Dataset

The dataset folder includes four different file which are readme, movies.dat, ratings.dat and users.dat. The dataset generally represents movies, users, the rating for each movie, the number of audience of each movies.

## User based collaborative filltering
To create the user based collaborative filltering, user-user table is important.

<img width="889" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/90def206-6dca-4474-ae18-8b6e1b19b179">

the key code to create the user-user table is provided below

```
user_similarity = matrix_norm_user.T.corr()
user_similarity.head()
```

The fundamental process of the user-based recommendation system involves selecting a specific user, identifying a set of similar users, examining the movies watched by these similar users, and finally providing recommendations based on their ratings. This code implements the algorithm, offering predictions for the entire rating spectrum for a randomly chosen user. Alternatively, users can be specified for more targeted predictions. To assess the accuracy of the predicted ratings, Root Mean Square Error (RMSE) values are employed. Additionally, the optimal number of similar users is determined through experimentation with values such as 5, 10, 15, 20, and 25.


<img width="459" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/90c69a98-e6f8-4788-ac53-4066d791d915">


<img width="428" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/f43eccb7-8364-4fff-8f6c-e5f8941e35dd">


## Item based collaborative filltering

The fundamental mechanism of the item-based recommendation system is nearly identical to that of the user-based recommendation system. Initially, an item-item similarity table is created, and a specific user is selected. After selecting the user, the system examines the user's highly-rated movies and provides recommendations of similar movies based on the item-item similarity table. In the generation of the similarity table, various methods can be employed, and among them, I have chosen Pearson and cosine similarity. Using this algorithm, a new program has been implemented wherein a random movie is selected, and ratings are predicted for all users. To evaluate the results, the Root Mean Square Error (RMSE) value is utilized.

Using pearson based itme-itme similarity table.

<img width="254" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/86cafdbb-4734-413e-8e2a-ab1defba119f">

The key code to create pearson based item-item similarity table is provided below.
```
item_similarity = matrix_norm_item.T.corr()
item_similarity.head()
```

Using cosine based item-item similarity table.

<img width="238" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/ff740620-4b70-4d8a-a8c7-1daac89aed73">

The key code to create cosine based item-item similarity table is provided below.

```
item_similarity_cosine = cosine_similarity(matrix_norm_item.fillna(0))
item_similarity_cosine
```

Since the cosine based item-item similarity table shows lower RMSE value, it can be said that the cosine based item-item similarity table is better than pearson based item-item similarity table in this case.

--------------------------------------------
## My recommendation system

In this task, I implemented new recommendation system using both user-based collaborative filltering and item-based collaborative filltering. The main purpose of this task is choose 1 random user and provide 30 recommendation movies. To reach this goals I got the idea from the content based recommendatio system, also, my recommendation system using the both user-based collaborative filltering and item based filltering.

Firstly, select the random user. Secondly, list top 500 recommendation using the user-based collaborative filtering with 10 similar user. Thirdly, store the list into the table. When storing the recommendations into the table, the order must be descending order.

The example table result in user-based collaborative filtering

<img width="447" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/307280e9-6252-4e36-a306-cb10502e5bb6">

After that, create the top 500 recommendation system using item-based collaborative filtering, and stored that data into the table with discending order.

The example table result in item-based collaborative filtering.


<img width="447" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/64b4dc28-5a1d-4e3a-a097-0b98e4ad7179">

Finally, create an empty table that includes movie names and points, and then merge the tables. At this point, the point colums stores the sum of the index value of the user-based and item-based recommendation result.

The example of the result table.

<img width="804" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/7e90bab8-a1c7-44f7-8e1b-c4f39395bde5">

By referring to the 'point' column in the final result table, you can identify the top 30 movie recommendations.

<img width="645" alt="image" src="https://github.com/hyeonBin7201/Data-science-Recommend-system/assets/152157238/4ba2690e-465a-4156-b1d8-76f78a07e390">



