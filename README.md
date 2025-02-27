# DS-3001-Project-1
## 01: Project Wrangling/EDA
#### The data are available, but a major part of the project is getting them cleaned: Perhaps it's voting data from many sources covering many counties or precincts. Your submission will focus on some basic features of the data and your cleaning plan.

For this project, I've decided to work on a dataset from Kaggle that scraped reviews off of Steam. There are 23 columns and the data is extensive, resulting in a file size of about 8GB. My **goal for the 01 submission** of this project is to truncate the data into more readable columns and getting basic sentiment data.

The process goes as follows. 'clean_and_tokenize_data.ipynb' gets the raw truncated data 'truncated_data', cleans and tokenizes it for the sentiment. Then the R script 'sentiment_analysis.R' turns it into a CSV 'sentiment_analysis_results.csv' which I later plan to combine back into one sheet.
https://www.kaggle.com/datasets/najzeko/steam-reviews-2021/data

##### A good submission will clearly address three questions:

1. What is in your data?
- Review text (freeform user-written reviews)
- Review score (positive/negative sentiment)
- Game information (title, genre, developer, release date, etc.)
- User information (playtime, number of reviews submitted)
- Timestamps (when the review was written, game release date)
  
  Why this dataset?
- It allows us to analyze player sentiment and see which game elements drive positive or negative reviews.
- The text data enables sentiment analysis (using models like BERT).
- The structured metadata (e.g., playtime, genre) allows for statistical comparisons.

2. How will these data be useful for studying the phenomenon you're interested in?
- The goal is to analyze and relate game elements to review scores on Steam to gain insights into player satisfaction.
  Specific analyses planned:
  - Named Entity Recognition (NER): Extracting key game-related terms (e.g., "multiplayer", "DLC", "graphics") to see how they correlate with sentiment.
  - Statistical Hypothesis Testing: Testing relationships between factors like genre, price, playtime, and sentiment.
    
3. What are the challenges you've resolved or expect to face in using them?
- The size of the data can be concerning, also truncating it to just English will result in overall accuracy.
- Using multiple languages can be a bit messy, I plan to work in python on cleaning the data and get some basic work done for the sentiment analysis and put it all into one table.
