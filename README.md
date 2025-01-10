# Project Description
This repository contains the implementation of a hybrid recommendation system for e-commerce platforms. It includes collaborative and content-based filtering techniques to provide personalized product recommendations based on user behavior and product features.
## Dataset
The dataset contains products purchased from Amazon, productId, and UserId to scores, reviews, and summary
## Data Exploration and cleaning
### Univariate Analysis
<div align="justify">
The following have been computed for analysis
1. Box plot for helpfulness numerator, which details the median, first quartile, third quartile, and maximum, including outliers.
2. Word cloud from customer Summaries, in which the size of each word indicates its frequency or importance.
</div>

### Bivariate Analysis
The analysis used plots, which correlate the data in numeric form.

### Multivariate Analysis
<div align="justify">
The analysis of Score, Helpfulness Numerator, and word count used a heatmap to derive the meaning of numeric and text-derived features.
At the same time, I analyzed the insight between the sentiment and score using the reviews by plotting a scatter plot.
</div>

## Method
### Recommendation Approach 
<div align="justify">
Instead of choosing an approach, I implemented both to check how the recommendation changes.
  
**1. Collaborative Filtering**
+ We use the Surprise library to implement this approach. The reader takes the score value range that the customer and the Dataset module gave expects three arguments: UserIDD, ProductID, and Score. The other metadata has been ignored as they are not directly used. Limited the samples to 50000 due to resource constraints.
+ The sim options take two arguments: the type of similarity you want to implement and whether you wish user-user/Item-Item collaborative filtering.
+ We used cosine Similarity and not pearson/mean sqaured metrics as cosine similarity measures the cosine of the angle between two vectors in context of ratings, this shows the evaluation whther the two users/items have similar rating patterns regarless of magnitude.
+ I implemented the KNNBasic algorithm, which finds the k most similar users based on a similarity metric. The rose metric was used to evaluate the accuracy, and this rose score(x) suggests that, on average, the predicted ratings deviate from actual ratings by approximately x on the rating scale (here, 1 to 5). 

**2. Content-Based Filtering**
+ Prepare the data to dot duplicates or na values, as TF-IDF can throw errors. Then, the text is converted to TF-IDF vectors, which convert the text into a numerical matrix representation.
+ Each term is weighed by its TF(Term frequency)-how often a term appears in the document and IDF(Inverse Document Frequency)- which reduces the weight of standard terms like “the,”  “is,” etc.
+ This creates a TFIDF matrix where the products are rows and columns with unique terms.
+ The algorithm we use here is Nearest neighbors and cosine similarity, as our goal is to get the patterns/trends.
</div>

## Predictions
<div align="justify">
Collaborative Filtering- This recommendation approach aims to give a score out of 5 when a user and product are provided. The output determines how well the user may like the product.
Content-BasFilteringing- This recommendation approach aims to provide a list of products similar to the one passed as input.
</div>
