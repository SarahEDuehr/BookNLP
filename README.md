# Predicting Readership of Books Based on Book Description


## Summary
This project atempts to predict the number of readers of a book using its description. Machine learning and natural language processing algorithms were used to create several classifiers. The results attempted to indicate if particular words or phrases in a book’s description predict how many people will rate a book. 

## Data 
The data was from the most popular site for book readers, GoodReads.com. The project used the datasets goodreads_books_romance and goodreads_books_children from sites.google.com/eng.ucsd.edu/ucsdbookgraph/home, which included average rating, number of ratings, and a description for over 300,000 romance books and over 124,000 children’s books. The features I ended up using were description text, description word count, and book rating count. 

## How It Was Made 
This project had three phases: data preprocessing, text analysis, and model building. 

**The data preprocessing phase**
1.	Importing the book data from .json files
2.	Removing books with language codes other than English, and books with descriptions too short to properly analyze.
3.	Reducing to only features needed: review count, average rating, description and rating count. 
4.	Preparing text by removing the punctuation and stop words (“the”, “of”, “and” etc.) and stemming and lemmatizing the remaining words. I used NLTK for this. 
5.	Removing outliers with a lot of ratings. I removed any books with rating counts three or more standard distributions from the mean number of rating counts. 
6.	Adding a feature with the word count of the descriptions. 

**The text analysis phase**
1.	Analyzing the text using the bag-of-words method to create a corpus of words used in all the book descriptions. 
2.	Creating topics from the text by using CountVectorizer() and TfIdfVectorizer() from the scikit-learn library. This method is useful when the documents contain a lot of very frequent terms, as is true in this project.

**The model building phase**
1. Splitting the data into 70% training data and 30% test data. 
2. Building five different classifiers: logistic regression, multinomial naïve bayes, linear support vector machine, stochastic gradient descent, and a sequential neural network.

## Evaluation
This project used six evaluation metrics to determine how accurate the models were at predicting the number of book ratings: confusion matrix, accuracy percentage, precision, recall, f1-score, and ROC area-under-curve score. Below a table of the results for each classifier for easy comparison.

## Lessons Learned
This data was difficult to classify using machine learning algorithms. This could be due to decision I tried to predict, how many people read the description and decided to read the book and rate it on GoodReads. This is not a simple decision. The customer’s choice is influenced by many factors not included in this project, such as price or available platforms (paper vs digital etc.). The choice is also not made quickly and is therefore harder to predict. In order to more accurately predict if customers choose to buy a book based on its description, I would need more direct data. The actual sales data of these books would be ideal.

## Results
Romance Books:

| Classifier              |  Accuracy Score |  Precision  | Recall   | F1 Score   | ROC AUC  |
|-------------------------|-----------------|-------------|----------|------------|----------|
| Logistic Regression     | 0.5988          |  0.6        | 0.6      | 0.6        | 0.599    |
| Multinomial Naïve Bayes | 0.5069          |  0.59       | 0.51     | 0.35       | 0.504    |
| Linear SVC              | 0.5219          |  0.59       | 0.52     | 0.41       | 0.5192   |
| SGD                     | 0.4970          |  0.5        | 0.5      | 0.33       | 0.5      |
| NN                      | 0.497           |  0.25       | 0.5      | 0.33       | 0.5      |


Children’s Books:

| Classifier      		    |  Accuracy Score	 | Precision	  | Recall	 | F1 Score  |	ROC AUC  |
|-------------------------|------------------|--------------|----------|-----------|-----------|
| Logistic Regression		  | 0.6012	         |  0.60	      | 0.60 	   | 0.60      | 0.6112    |
| Multinomial Naïve Bayes	| 0.5113           |  0.59    	  | 0.58  	 | 0.57 	   | 0.5163    |
| Linear SVC		          | 0.5724	         |  0.58	      | 0.57 	   | 0.56 	   | 0.5703    |
| SGD			                | 0.5390           | 0.55         | 0.54     | 0.53	     | 0.5409    |
