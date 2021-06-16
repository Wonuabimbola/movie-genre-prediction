# Text Classification of Movie Plot Summaries to Predict Movie Genres

### Author: [Wonuola Abimbola](https://github.com/Wonuabimbola)

## Overview

Movies are one of the most popular means of entertainment. There are large volumes of movie data being generated and shared on the internet.The genre of a movie can be deciphered from its synopsis most of the time. This project seeks to perform text classification of movie plot summaries in order to predict movie genres. NLP techniques were applied to the movie plot summaries in order to use them predict the movie genres. The dataset is from Kaggle which contains plot summary descriptions scraped from Wikipedia. Automated movie genre predictions can also have applications in movie recommendation systems. In this project, only the movies that were assigned one genre were used in order to perform multiclass classification.

## Preprocessing

In this stage, the data was subset to include only the movies that have one genre. They also happen to have the top six highest value counts in the dataset. Adding 'labels' column to our dataset, we assigned labels to our 6 classes assigning 1 for 'drama', 2 for 'comedy', 3 for 'horror', 4 for 'action', 5 for 'thriller' and 6 for 'romance'. The 'Plot' column was then 'cleaned' using NLP preprocessing techniques (removing stopwords, punctuation, changing the text to lower case and so on)

## Exploratory Data Analysis

Looking at the frequency distribution of the top six genres in the data, the most prevalent genre is 'drama' with 'comedy' following close behind. The least prevalent genre is 'romance'.

![distribution of top six genres in the dataset](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqoftopgenres.png)

The visuals below show the word frequency distribution of plot summaries per genre

![PlotWordFreqDrama](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryfordramagenre.png)

From the plot above, we see that drama genres commonly revolve around family, life

![PlotWordFreqComedy](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforcomedygenre.png)

Most common words here are mostly similar to those in drama e.g. family, life, father.

![PlotWordFreqHorror](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforhorrorgenre.png)

The horror genre seems to have words like 'kill'/'killed', 'death' and 'body commonly mentioned in the plot summaries

![PlotWordFreqAction](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforactiongenre.png)

The words 'killed', 'police' appear commonly in the plot summaries of this genre. There is also similarity in most common words between action and horror 

![PlotWordFreqThriller](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforthrillergenre.png)

Thriller has words in common with the last two genres we've seen I.e. action and horror

![PlotWordFreqRomance](https://github.com/Wonuabimbola/movie_plot_project/blob/main/images/freqdistofwordsinplotsummaryforromancegenre.png)

Looking at the words in romance genre. It's no surprise that some of the most common words in the plot summaries are 'love', 'life', 'marriage'.

## Modeling and Results

The first simple model which predicted the most frequent class gave us an accuracy score of 41% which served as the baseline

### After performing grid searches on the following models and evaluating them:

* Multinomial Naïve Bayes

* Logistic Regression

* Decision Tree

* Random Forest Classifier

The decision tree and random forest models performed least favorably. The Logistic Regression Model performed best when used on the tfidf-transformed X variable, achieving an accuracy score of ~63%. GridSearchCV helped in narrowing down the best hyperparameter values. When the model was applied to the test set, a 64% accuracy score was achieved. This is a significant increase from the baseline accuracy of 41% gotten during cross validation!

## Next Steps

* Utilizing Neural Networks to possibly achieve greater accuracy

## Navigation


```
├── README.md                                           <- This README file
├── data                                                <- obtained from kaggle.com
│   ├── wiki_movie_plots_deduped.csv                    <- contains movie plot data scared from Wikipedia
├── gitignore                                           <- files to ignore
├── predict_movie_genre_from_plot_summary.ipynb         <- final notebook
├── predict_movie_genre_from_plot_summary.pdf           <- presentation
└── images                                              <- Visualizations used in README and pdf file



