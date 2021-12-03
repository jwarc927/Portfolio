## Subreddit NLP Classification 

### Problem Statement

The goal of this project is to determine if we can train a classifiation natural language processing algorithm to classify news headlines by inentionally satirical articles written by The Onion versus real articles that the Reddit community has identified as seeming satirical.  The goal will be maximize accuracy for the training set because there is no clear preference toward minimizing false negatives versus false positives. 

### Data Used

The dataset we are using has been extracted from Reddit using the Pushshift API.  In particular, the subreddit [theOnion](https://www.reddit.com/r/TheOnion/) and [nottheonion](https://www.reddit.com/r/nottheonion/) were used.  The Onion subreddit has approximately 20,000 posts and Not The Onion has nearly 500,000 posts.  From this set of possible posts, we extract approximately 15,000 entries starting from the most recent from each subreddit.  Most of these posts do not have body text, so the data only includes the title, which corresponds to the headlines of the original article.  T

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**title**|*string*|both|The headline of an article| 
|**onion**|*boolean*|both|1 if the headline is from the Onion, 0 if it is not|

### Summary Analysis

Three different approaches were attempted.  The first was to perform a sentiment analysis on the headlines to see if there may be trend in Onion article to have more sentiment in total (either positive or negative).  This approach did not prove useful because the sentiment for both types of headline were distributed in a very similar way.  The second approach was to use word vectorization to determine if there was a pattern of non sequiturs in the Onion headlines.  The thought process here is that in this method words are vectorized in 50D space based on their proximity to other wrods in a corpus of text.  If there were a lot of words that were in contextually unusual places, this could be an indication of satire.  Unfortuneatly, this analysis was too computationally intensive for the computer resources availalbe and was tabled for possible reinvestigation at a later date.

The third method consisted of training three different models (Random Forest, Support Vector Machine, and Logistic Regression) on a Term Frequency-Inverse Document Frequency (TF-IDF) Vectorizer transformed version of all of the headlines.  Finally, an Ensemble model consisting of these three base models is fit.

### Conclusions

Selected metrics from the models generated above are presented below:

|Model|Accuracy|Recall|Precision|F1 Score|
|---|---|---|---|---|
|**SVM**|70.6%|56.4%|78.6%|65.7%| 
|**Logistic Reg**|65.8%|56.2%|74.5%|64.1%| 
|**Random Forest**|64.6%|38.9%|79.9%|52.2%| 
|**Ensemble**|69.2%|53.7%|77.7%|63.5%| 

Based on these results, the recommended model is the SVM because it is better than every other model in every metric except for the precision of the Random Forest model.  However, the Random Forest model's poor recall and low accuracy disqualify it as the best.