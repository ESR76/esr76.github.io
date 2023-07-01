---
layout: post
title: Shark Tank Deal Predictions (48 Hour Project)
description: As a part of UC San Diego's Data Science Student Society (DS3) annual data science hackathon, DataHacks, I and two other undergraduates attempted to predict whether a pitch would get a deal on Shark Tank or not based on the pitch.
---

#### Abstract

Shark Tank is a popular show where a panel of celebrity "Sharks" judge entrepreneurs’ pitches for their small businesses. Given the Shark Tank (US) pitches and deals made over the course of 8 seasons, our team used natural language processing to generate predictions based on the content of the business descriptions as to whether or not the pitch was successful in getting a deal or not.

##### Data

Our data for this project was a subset of the data provided in this [Kaggle dataset](https://www.kaggle.com/datasets/neiljs/all-shark-tank-us-pitches-deals). For each pitch, we had a season number and episode code string, a product title string, a pitch string, a boolean deal status, and the initials of the Shark(s) who made the deal. 

We found that:
* Companies with shorter names tended to get deals more often (1-2 word products over 3+ word products).
* Successful pitches had an average longer pitch length.
* The overall proportion of deals rose gradually over each season, and the judges who contributed the most to making deals changed over time as well.

Our most extensive data analysis for this project was on the pitch data, where we utilized tokenization and removed stop words to try and create effective word embeddings. We used Word2Vec to analyze the pitches' word vectors in 2 dimensional space (t-SNE), as well as using a Google News-trained word bank via Gensim. We also tried Latent Dirichlet Allocation as a way of analyzing the pitches to create preferred topics for each shark, but did not continue with this approach as we ran into issues in the time we had.


##### Models

The model we used was a Decision Tree Classifier and we submitted two versions. The first was a simple Term Frequency-Inverse Document Frequency based Decision Tree Classifier on the pitch data. The second used the Google News word bank with Gensim's Word2Vec model to create word embeddings of each pitch -  we then trained a decision tree classifier on the average vectors for each word in a pitch, the season, episode number, length of business title, and length of business description.


#### Results Overview

Both of our Decision Tree Classifier models had similar training accuracies in the 80-90% range depending on the trial we ran. The biggest challenge of this project was absolutely the time constraint, but the project also pushed us to try new data science techniques and play around with them in a way we never had before.

This project does not have any real form of published results except for the quickly-written paper turned into the judges at the end of our 48 hour period - if you'd like to view this, please let me know and I can try to provide a copy.

This project was a part of the hackathon's (DataHacks') intermediate track, and our team was one of 3 teams on the track to receive an honorable mention.