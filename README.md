# WeRateDogs_tweet_analysis

The aim of the project is to wrangle WeRateDogs Twitter data to create analyses and visualizations. 

Three different datasets were gathered, assessed, cleaned, combined and used to achieve visualizations. This was done with the use of Python and its libraries.

1. A Twitter archive containing basic tweet information was given in the form of a .csv file [twitter-archive-enhanced.csv](twitter-archive-enhanced.csv) by the udacity. This was downloaded from the Udacity website, and then cleaned programmatically, while following the process - Assess, Clean, and Test.

2. A .tsv file having dog images prediction information was also given - [image-predictions.tsv](image-predictions.tsv). It was also downloaded, uploaded and loaded to the jupyter notebook interface and assessed and cleaned programmatically. This file contained the image prediction information gotten from running the WeRateDogs Twitter archive through a neural network that can classify breeds of dogs.

3. The third dataset was gotten by querying the twitter API using the tweet_id information gotten from the WeRateDogs Twitter archive, and finding relevant information about the tweets, including favourite_count and retweet_count. The JSON data was collected with Pythons tweepy library and each tweet's JSON data was added to a file called [tweet_json.txt](tweet_json.txt) file.

All three datasets were assessed programmatically and visually.

Data assessing is looking through the data carefully in a way to discover messiness and dirtiness and clean the data.

Dirtiness in data is the presence of incorrect, inaccurate or missing data.

Messiness however has to do with structural problems with the data. When a data is completely cleaned from any messiness, it is said to be tidy. The requirements for tidy data are:

>Each variable forms a column.
    Each observation forms a row.
    Each type of observational unit forms a table.

Messiness and dirtiness in the data generally prevent easy analysis and errors in visualizations. 

#### Quality issues found are:
##### df_image_pred
* Poor Column Names - Column names that do not have clear descriptions are renamed, such as p1, p2, etc.
##### All data tables
* Wrong datatypes - The tweet_id in all the dataframes are curently of the numerical data type, these are converted to string. Wrong datatypes in timestamp is changed from object to timestamp
##### df_tweet_rating
* Unwanted information regarding retweets in df_tweet_rating in retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp columns, since only the original tweets required, these are dropped.

* Rating_numerator values were incorrectly extracted from text column and do not show the decimal numbers. I re-extracted the correct rating_numerator values from the text column.

* High amount of missing values data in_reply_to_status_id, in_reply_to_user_id columns. These are dropped

* Dog names: The dog name column contain sentence articles that are not dog names. We would drop the rows with false dog names e.g. a, the, etc. The dog names recorded as None are kept however, because in some cases, dogs are not yet named by the owners.

* Source column: Entries in the source column are replaced with understandable descriptions. 

* Retweets and Favourite Counts - The retweet and favourite counts cannot be floats as we cannot have decimal numbers in this column, therefore, these are converted to integer data types.

* Unnessary/duplicated column information. The information in the df_twitterapi created_at column is the same as the one in df_tweet_rating timestamp column, but poorly formatted. The df_twitterapi created_at column is therefore dropped.

#### Tidiness issues found are:
* The doggo, floofer, pupper, and puppo columns were combined to improve tidiness

* Since each observation unit should represent a table, the df_tweet_rating, df_archive and df_twitterapi were merged.

Summarily, Cleaning actions were performed such as changed data types, and column restructure in some columns. Inbuilt methods such as .replace(), .drop(), .drop_duplicated(), .rename(), etc., were applied.

The entire wrangling act is documented in the [wrangle_act.ipynb](wrangle_act.ipynb)

A report on the data is also provided in the [act_report (1).ipynb](act_report (1).ipynb)
