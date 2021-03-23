# Rescoring_Yelp_Stars_with_NLP_Models
An initial effort to use NLP methods on user reviews to normalize star score bias.  There are many misaligned reviews and star scores, along with easy five star scores. I wanted to test Classification models to give a better star distribution. I used the Yelp Academic Dataset found here - https://www.yelp.com/dataset 

Examples of misaligned reviews:
![misaligned reviews](https://user-images.githubusercontent.com/3197895/112232053-280b2700-8bf5-11eb-9186-559d948cf91b.png)

Also, in general star scores skew towards 5 stars way too often. 
![general star distribution](https://user-images.githubusercontent.com/3197895/112232146-4e30c700-8bf5-11eb-8ee6-f8477e61209c.png)

If we look more categorically,
![star scores by category](https://user-images.githubusercontent.com/3197895/112232214-6d2f5900-8bf5-11eb-820b-0ad839ae13a6.png)

After importing, merging, and sampling the datasets to a manageable size; I filtered for food based business reviews. 
- I then engineered a feature based on user avg scores vs if they scored the current business higher than the business average score.  This binary feature is called 'fan' - and was my target variable in my models.
- I put the reviews through tfidf vectorization after normalizing with a tokeninzer and lemmatizer.
- I then ran a Random Forest Classifier and a 2 input,1 ouput LSTM / Sequential neural net.  

The Random Forest gave better results at a baseline and is much less resource intense.  

With the results, I built a function to normalize the star scores based on reviews. See the new distribution.
![ML star scores](https://user-images.githubusercontent.com/3197895/112232756-59d0bd80-8bf6-11eb-9105-02a619290dd2.png)
