# Text Classification of Movie Plot Summaries to Predict Movie Genres

### Author: [Wonuola Abimbola](https://github.com/Wonuabimbola)

## Business and Data Understanding

Movies are one of the most popular means of entertainment. There are large volumes of movie data being generated and shared on the internet every second.The genre of a movie can be deciphered from its synopsis much of the time. This project is a multiclass text classification problem which uses movie plot summaries to predict movie genres. NLP preprocessing techniques were implemented on the summaries to improve predictive capability. The dataset is from [Kaggle](https://www.kaggle.com/jrobischon/wikipedia-movie-plots) which contains plot summary descriptions scraped from Wikipedia. In this project, only movies that were assigned one genre were used.

Columns:
* Release Year - year of release
* Title - title of the movies
* Origin/Ethnicity - country of origin of the movies
* Director - director names associated with the movies
* Cast - cast name associated with the movies
* Wiki Page - wikipedia page of the movies
* Plot - plot summary of the movies

## Preprocessing

- The data was subset to include only the movies that have one genre. 
- I label-encoded the genres. 
- The 'Plot' column was then 'cleaned' using NLP preprocessing techniques (removed stopwords, punctuations, digits, changed text to lower case, lemmatization, tokenization)

## Exploratory Data Analysis

Frequency distribution of the genres showed the most prevalent genre was 'drama' with 'comedy' following close behind. The least common genre was 'romance'.

![distribution of top six genres in the dataset](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqoftopgenres.png)

The visuals below show the word frequency distribution of plot summaries per genre. There were quite a few commonly occuring words among the genres.

![PlotWordFreqDrama](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryfordramagenre.png)


![PlotWordFreqComedy](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforcomedygenre.png)


![PlotWordFreqHorror](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforhorrorgenre.png)


![PlotWordFreqAction](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforactiongenre.png)


![PlotWordFreqThriller](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforthrillergenre.png)


![PlotWordFreqRomance](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforromancegenre.png)


## Modeling and Results

The metric used in this project is the 'accuracy score'

The first simple model which predicted the most frequent class achieved an accuracy score of 41% which served as the baseline.

### Grid search on both tfidf and count_vectorizer transformed data:

Best model was logistic regression with tfidf transformed summaries with the following parameters:
* C = 1.0
* class_weight = 'balanced'
* multi_class = 'ovr'
* penalty = 'l2'
* solver = 'liblinear'

![Comparisonofmodelscores](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/model_scores.png)

### Testing Result

I implemented the model on test data and achieved an acurracy score of 64% which is a significant increase from the baseline

![Confusionmatrixoftestpredictionsvsactual](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/confusionmatrix.png)

### Cosine Similarity of the genres using words in their plot summaries

This showed that the plot words in each genre were highly similar to the others

![cosinesimilarityofthegenresusingplotwords](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/cosinesimilarityofthegenresusingplotwords.png)

## Conclusion
* The confusion matrix above confirms what I suspected when looking at the most common words among the genres.
* Due to the fact that some of the genres had words in common with another genre, false predictions of those genres were mostly as the genres they had common words with.
* The decision tree models performed the least favorably.


## Navigation


```
├── README.md                                           <- This README file
├── data                                                <- obtained from kaggle.com
│   ├── wiki_movie_plots_deduped.csv                    <- contains movie plot data scraped from Wikipedia
├── gitignore                                           <- files to ignore
├── predict_movie_genre_from_plot_summary.ipynb         <- final notebook
├── predict_movie_genre_from_plot_summary.pdf           <- slide decks
└── images                                              <- Visualizations used in README and pdf file



