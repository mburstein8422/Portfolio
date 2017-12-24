# Semantic Search

## The Task
The objective of the project was to engineer a novel wikipedia search engine using MongoDB and natural language processing.

The task has was compelted in the following two phases:

![](http://interactive.blockdiag.com/image?compression=deflate&encoding=base64&src=eJxdjrsOwjAMRXe-wlsmRhaQkDoiMSDxBW5slahtHDmGCiH-nfQxtKy-59zruhPfUsAGPjsA56XvMdIRSIbYCZKD_RncENqQuGBQ3S7TidCwxsynjZUZ1T8m4HqvJlXZnhrBJMHBbWlTDHEeSFravYUXQy_E3TKrwbioMKb5z16UmRxfXZurVY_GjegbhqJIjaXm-wNmzE4W)

### Phase 1 -- Collection 

Query the wikipedia API and collect all of the articles under the following wikipedia categories:

* [Machine Learning](https://en.wikipedia.org/wiki/Category:Machine_learning)
* [Business Software](https://en.wikipedia.org/wiki/Category:Business_software)

The raw page text and its category information was stored on a Mongo server running on a dedicated AWS instance.

**Note:** Both "Machine Learning" and "Business Software" contain a heirarchy of nested sub-categories.

**Results:**. Over 1,100 articles were collected under the category Machine Learning and over 8,400 articles were collected for Business Software.  The data collection was done through the wikipedia API and all article content, pageIDs, and article titles were stored using MongoDB.  The code is modular enough that any valid category from Wikipedia can be queried.


### Phase 2 -- Search 

Use Latent Semantic Analysis to search your pages. Given a search query, find the top 5 related articles to the search query. SVD and cosine similarity are a good place to start. 


**Results:** The following steps were completed to search the wikipedia pages:
  
  1) Query the category to search within by collection name.  Note collections were Machine Learning and Business Software.
  
  2) Tokenize the article content using the TfidfVectorizer with n_gram range of (2,2)
  
  3) Use TruncatedSVD to reduce the tokenized article content to 120 components.
  
  4) Enter in search terms
  
  5) Use cosine similarity to identify the articles most similar to the search term.
  
 Thee top five articles for each category had a cosine similarity ranging from 0.6-0.8. 
 
### Next Steps

  1) Optimize text vectorization by further tuning the n_gram range and min_df.
  
  2) Optimize components through increasing the TruncatedSVD to 200 components.
  
  3) Further testing of cosine similarity results.
