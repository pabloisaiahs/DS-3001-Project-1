# DS-3001-Project-1
## 01: Project Wrangling/EDA
#### The data are available, but a major part of the project is getting them cleaned: Perhaps it's voting data from many sources covering many counties or precincts. Your submission will focus on some basic features of the data and your cleaning plan.

For this project, I've decided to work on a dataset from Kaggle that scraped reviews off of Steam. There are 23 columns and the data is extensive, resulting in a file size of about 8GB. My **goal for the 01 submission** of this project is to truncate the data into more readable columns and getting basic sentiment data.

The process goes as follows. 'clean_and_tokenize_data.ipynb' gets the raw truncated data 'truncated_data', cleans and tokenizes it for the sentiment. Then the R script 'sentiment_analysis.R' turns it into a CSV 'sentiment_analysis_results.csv' which I later plan to combine back into one sheet.

https://www.kaggle.com/datasets/najzeko/steam-reviews-2021/data

![image](https://github.com/user-attachments/assets/5dd091d6-850e-48a4-bbb8-7ca2930d73e0)

![image](https://github.com/user-attachments/assets/34be171d-6256-4108-ad82-15b7bec3e9fc)


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

## 02: Establish Data & Register Analysis Plan

##### Research Question
How do individual gameplay elements influence the sentiment of Steam reviews, and to what extent can review sentiment be used to predict overall game recommendation ratings?

##### Observation Unit
Each observation in our dataset is a single English-language Steam review that includes:
- Full text of the review
- Binary recommendation score (0 = not recommended, 1 = recommended)
- Sentiment score derived from BERT and R (syuzhet)
- Named entities extracted as gameplay elements (e.g., story, graphics)

##### Modeling Type
I'm conducting a supervised learning task, using:
- Binary classification to predict game recommendation (review_score)
- Hypothesis testing to evaluate the association between review sentiment and review ratings
- Exploratory analysis with elements of unsupervised learning (NER and sentiment extraction)

##### Models and Methods
1. Sentiment Analysis (Text Modeling)
- Pre-trained BERT or RoBERTa for sentiment classification on review text
- Rule-based sentiment using syuzhet in R for comparison and validation
2. Named Entity Recognition (NER)
- Use spaCy to identify gameplay-related terms
- Label detected terms under categories like Story, Graphics, Multiplayer, etc.
Append sentiment scores to these elements
3. Statistical Hypothesis Testing
- One-sample t-tests:
  - H0: Mean sentiment score for positive reviews ≤ neutral score
  - H1: Mean sentiment score for positive reviews > neutral score
- Two-sample t-tests:
  - Compare reviews with vs. without certain gameplay elements
4. Predictive Modeling
- Logistic Regression
- Random Forest

##### Feature Engineering
- One-hot encoding for genre/platform data
- Sentiment scores from two models (R and BERT)
- Binary presence flags for gameplay terms
- Normalized helpfulness scores

##### Success Metrics
- Accuracy, F1 Score, Precision, Recall, and ROC AUC for classification
- P-values from t-tests for statistically significant relationships
- Qualitative insights from review examples and visualizations

    | Challenge | Solution |
    | :--- | ---: |
    | Playtime missing from dataset | Limit scope to review sentiment + NER until enriched dataset is acquired |
    | Sarcasm or slang in reviews | Rely on transformer models like BERT to handle nuanced language |
    | NER ambiguity | Curate and refine a set of target gameplay keywords manually |
    | Overfitting on high-dimensional sentiment features | Apply regularization (L1/L2) and reduce dimensionality |
    | Large dataset (~2M reviews) | Sample subsets for faster iteration; move to full set after testing |

##### Results and Presentation
- Confusion matrices, classification reports, and ROC curves for model evaluation
- Word clouds, box plots, and bar charts for visual insights
- Tables of t-test results showing significance of gameplay elements
- Merged sentiment + gameplay visualizations (e.g., heatmaps or network graphs)


