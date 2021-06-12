---
layout: post
title: Spiegel Online Sentiment 05/21
excerpt_separator:  <!--more-->
tags:
  - Spiegel Online
  - Sentiment

---

### Intro

Sentiment analysis of 3585 articles that were published on Spiegel Online between 5/5/21 and 6/5/21. Including Spiegel Plus and deleted articles.

![ref](/_screenshots/ref.jpg?raw=true)

About half of all articles were published under the categories *Panorama*, *Ausland* and *Politik*.

![sum](/_screenshots/pie.png?raw=true)

### Sentiment per Category

I wrote an AI that assigned each word in every category a sentiment score between -1 and 1. The mean of all individual scores per word resulted in a score for each article. This article score is an indicator for the overall positivity/negativity of an article.

- -1	very negative
-  0	neutral
-  1	very positive

The following graphic shows the sum of sentiments per category. An article with 0.5 Sentiment, and another one with -0.5 Sentiment would even each other out to 0. An article with 0.2 and one with -0.4 would result in -0.2.

![sent_cat](/_screenshots/sents_sum.jpg?raw=true)

*Panorama* and *Ausland* are the only categories with negative sentiment. *Sport* articles are very positive and all other categories are overall positive.

The graphic below displays the mean sentiment per category as a box plot. The only category with all positive articles is *Tests*. The least positive Article in *Tests* has a sentiment score of 0.146, which is still in the top 16% of the most positive rated articles.

![sent_test](/_screenshots/ref_box.jpeg?raw=true)
