# Wrangling Process

## The wrangling process contains 4 main steps:
### -The first step is to gather the data, here we have 3 main sources:

- Loading the `twitter-archive-enhanced.csv` file
- Download&Save then load `image-predictions.tsv` file
- query a data from tweeter: using tweepy API to access certain status about some tweets


### -The second step is to assess the data quality and tidiness:

#### we can assess data both programmatically or visually, and there were several problems:
##### 1- Quality issues

- `in_reply_to_status_id` column consist of random numbers
- `in_reply_to_user_id` column consist of IDs that dosn't exist
- `timestamp`column is string not datetime
- `retweeted_status_id` column also consist random numbers
- `retweeted_status_user_id` column also consist of IDs that dosn't exist
- `retweeted_status_timestamp` column consists of misxed datatypes (str&float) not datetime
- `rating_numerator` & `rating_denominator` colmuns have invalid values
- `names` column have invalid dog names
- `tweet_id` is int
- some values are `None`
- columns have undescrpitive names
- `p1` & `p2` & `p3` have non-dog-name values

##### 2-Tidness issues

- `doggo` & `floofer` & `pupper` & `puppo` in 4 different columns
- all DataFrames should be in one DataFrame

### Thirs step comes after assessing the data we convert these to verbal commands that we can execute, we can do the following:

- drop `in_reply_to_status_id` colum
- drop `in_reply_to_user_id` colum
- convert `timestamp` column to datetime
- drop `retweeted_status_id` colum
- drop `retweeted_status_user_id` colum
- convert `retweeted_status_timestamp` column to datetime
- repull `source` values and reconstruct the column (already done)
- `p1_conf` alwayas has the higher conf
- drop images the dosn't contain dogs (i.e. `p1_dog` == False)
- drop `p1_conf` & `p1_dog` after confirming on `p1`
- fix `source` column
- megre all DataFrame into one DataFrame

### - The fourth step is we discover some insights
- What was the most favorite tweet?
- What was the most retweeted tweet?
- Five most common breeds found by the neural network.
- Common breeds by percentage.
- Most users' source
