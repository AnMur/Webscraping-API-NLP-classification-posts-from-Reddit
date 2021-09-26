# Andrei Muravev



## Classification Models and NLP




 ### Problem Statement

   In our days popularity of remote learning, jobs and shopping increasing every day. With this, more and more people start to use different online platforms for communications. One of the most popular communication platforms is reddit. For my project, I'm going to take two the most popular subreddits: 'books' and 'parenting' and try to identify if words in posts from books and parenting different enough that analytical models can predict which subreddit a post came from? To be more specific, I'm going to scrape aproximatelly 10_000 posts from this two subreddits and combine them. Set my target. It would be posts from subreddit 'books'. Later, if posts belong to 'books' it would be given number 1 and number 0 if posts belong to 'parenting'. Several classification models - KNN, Logistic Regression, Decision Tree and Random Forest will try to predict if posts came from subreddit 'books. I'm choosing to use only classification models for this project because this models suppose to group posts together on the basis of common features. To challenge myself and my prediction models, I'm going to scrape equal amount of posts for both subreddits. It means that the baseline score would be 0.5. The classification models would evaluate my data from 0 to 1 and need to beat this score. 
   
  Now, why scraping, analyzing and predicting subreddits based on words could be important and who might be interested in this? Broadly, it could be easily used for the sentiment analysis to detect positive or negative emotions in social data, detect new brands or understand customers. Scraping data from online communication platforms might be helpful in recognition of names, organizations and locations.
In my particular project, I will also use topic modeling. It is a type of statistical model in machine learning and natural language processing that counts words and groups similar word patterns to infer topics within unstructured data. Many companies implement this technique to organize large datasets of emails, customer reviews and social media profiles. New York Times, for example, are using topic modeling to boost their user – article recommendation engines. After analyzing my 'books' subreddit and if my classification models could predict very well words that belong to books, I could potentially collaborate with publishers, newspapers or book stores to help with advertising campaigns or to find new best sellers. 
  



 ##  Data sources

  https://www.reddit.com/r/books/
  
  https://www.reddit.com/r/Parenting/




  
 ## Project Map
 
 
 
### Notebook  'Loading and Collecting Data'
 
 - Scrapping subreddit 'books' to get 11250 posts
 - Scrapping subreddit 'Parenting' to get 5250 posts
 - Remove duplicates and empty posts, concatinate posts and create dataframes
 - Save dataframes to two csv files: "book.csv" and "parenting.csv". Both files are in data notebook

 

### Notebook 'Cleaning'
 
 - Importing datasets from data folder
 - Fixing the size of columns
 - Exploring columns
 - Creating a data dictionary for each column
 - Concatinatig both subreddits to create a new dataframe with columns I want to use later 
 - Check missing posts and duplicates
 - Combine 'title' and 'selftext' columns in one column 'text'
 - Working on text column and cleaning all text:
  * **Porter Stemmer**
  * **create a function 'clean_text' what use RegexpTokenizer**
  * **WordNetLemmatizer**
 - Comparing both cleaning methods and lemmatizer
 - Final Columns to keep
 - Convert column subreddit to 0 and 1
 - Created a new dataframe 'cleaned.csv' what is ready for EDA

 
### Notebook 'EDA'
 
 - Loading libraries and datasets
 - Creating two new dataframes that include just words from 'book' and another is words from 'parenting' subreddits
 - Checking Words distribution
 - Creating custom stop words list from the 'english' stop words plus word cloud's stop words
 - **Tf-Idf Vectorizer:**
    * Checking for outliers and vizualization using 
    * Exploring the most frequent words in books subreddit
    * Exploring the most frequent words in parenting subreddit
 - **WordCloud:**
    * Vizualization of the most common words in Book Subreddit
    * Vizualization of the most common words in Parenting Subreddit
    
    
### Notebook 'Modeling'

 - Loading info
 - Evaluating a Baseline score 
 - Establishing target, features, train, test and split our model
 - Instantiating the Count Vectorizer
 - Instantiating the Tf-Idf Vectorizer
 - Logistic Regression
 - KNN
 - Decision Tree
 - Random Forest
 - Conclusions after initial modeling
 
 
 
### Notebook 'X-Y  Final Modeling'

 - Loading Data
 - Adding 'read' and 'book' to stop words list
 - Setting target and train test split my model
 - Instantiating the Pipe(Tf-Idf and Random Forest) and Setting Parameters for the Grid Search
 - Fitting the Grid Search and Evaluating scores
 - Predictions and Model Evaluation using Confusion Matrix
 - Looking at the posts...
 

## Conclusion

  ### After collecting all results, it is possible to state:
  
  - all models successfully predicted posts that belong to subreddit 'books'. Logistic Regression and Random Forest received 0.98, Decision Tree 0.95  and KNN - 0.53 Moreover if posts belong to 'parenting' subreddit , the models indicated it as well. It means that the best models outperformed the baseline score by more than %50  and this models could be useful in marketing and search bestsellers purposes if further exploration and analysis would be conducted. I've attached predicted results for each individual post to my data folder as a separate 'predictions.csv' file.

  - During my project, I've spent a lot of time cleaning my data. Of course, most posts came deleted, removed, included special signs such as ( /!,'''&5%$#), emojies or links. All of this could not be helpful for analyzing the texts. Here, I've experimented with three different techniques how to clean my data using Porter Stemmer, RogexpTokenizer and WordNet Lemmatizer. Lemmatizer would cut the endings of words and leave me the root. It is very convenient to use. But, I thought that for this project it didn't work very well because it made some words very short and it was very hard to understand the initial meanings of these words, for example, 'wa' instead of 'want'. Porter Stemmer was good too, but it also changed some words as 'why' to 'whi' and didn't remove all special signs and dotes. RogexpTokenizer was the best. It has a lot of setting that could be changed. I've spent a lot of time experimenting and found one that cleaned my posts as I wanted. 

  - During Exploratory Data Analysis, additional cleanings of texts were made using two types of stop words 'NLTK english stopwords' plus 'WORDCLOUD stop word's which were helpful in removing unnecessary words such as 'www', 'http', 'is', 'a' and other. After plotting my graphs, it was possible to see which words were most common in subreddit 'books' and subreddit 'parenting' and how many times people used it. It was very significant steps in preparation posts for modeling and creating slides for future stakeholder presentations.


### Future steps

  - In this project, I've had 4 outliers from subreddit books: 'read', 'readings', 'book', 'books'. It helped my models to perform very well. I experimented a little bit and removed them for Random Forest model, but it is still outperformed the baseline score. For future, I'd like to experiment and scrape texts from five or more different subreddits and see how well models could perform on even larger datasets.

 - Topic modeling is very powerful tool as well as predicting posts. Again, you could look at my predictions.csv file in data folder or at the EDA notebook to wordcloud graphs. It was very interesting, for example, to observe verbs from parenting subreddits. One of the most common was 'want' that wasn't popular in 'books'. I think further explorations of verbs and their correlations with topic could really build an image of people needs. These findings could be interesting for large retail companies, marketing or human resources.
 

