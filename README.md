# Book-Recommender-System--IFT511
Build a recommender system that recommends books to read for every user based on their personal tastes and previous book ratings. 

This project involves using data mining and machine learning techniques to analyze a large dataset of book ratings.

# Dataset Description
The Book Crossing dataset can be downloaded through Kaggle:

https://www.kaggle.com/datasets/somnambwl/bookcrossing-dataset?resource=downloadLinks to an external site. 

# It consists of three files:

Books.csv - Contains information about different books such as book title, description, author, ISBN, etc. 

Users.csv - Contains user IDs and ages.

Ratings.csv - Contains users' ratings of different books. 

# The dataset contains:

Over 270,000 books

Over 270,000 books 

Over 1 Million ratings given by users to books

The rating scale goes from 0 to 10.
 
# Data Preparation

Preparing the data for analysis depends on the chosen tasks.

Preparing Data for the Recommender System

Using the Ratings.csv file, created a User-Book sparse matrix where each row represents one user, and each column represents one book:

User	Book1Rating	Book2Rating	Book3Rating	..	..	..
User1		.  			         6	       .
User2		5				          .        . 
User3		.				          3        . 
.			   10             .	       .		
.						8              .        .
.	     .              2	    			.	  

Since this is a high-dimensional sparse matrix, the efficient way to store it is using a libsvm file format.

# Building a Recommender System

I built a Recommendation System using Collaborative Filtering with Proximity Calculations

For each user I did the following:

* Find the K most similar users to u. Let K be equal to 10. Use Cosine similarity proximity measure to achieve the same.
* For these K users, find the set of books that were read by any of them. This set is, BK.
* Calculated a weighted average over the rating of each book b in BK as follows

![image](https://github.com/user-attachments/assets/aa49f527-8581-4d6f-81dc-7b7ea3458bba)

Finally, find the 5 books with the highest estimated ratings, and were not read by u, and recommend them to u.
The code writes the recommendation results in a CSV file with this format:

User_ID, Book_ID, Book_Title, Recommendation_Score
