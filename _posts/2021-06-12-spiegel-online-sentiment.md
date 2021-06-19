---
layout: post
title: Spiegel Online Sentiment 05/21
excerpt_separator:  <!--more-->
tags:
  - Spiegel Online
  - Sentiment

---

### Intro

I downloaded all Spiegel Online articles that were published between 05/05 - 06/05/21 and ran a sentiment analysis on them. In total there are 3.585 articles for this month, including Spiegel Plus and deleted articles.

#### Articles per Category

![ref](/_screenshots/0521/ref.jpg?raw=true)

About half of all articles were published under the categories *Panorama*, *Ausland* and *Politik*.

![sum](/_screenshots/0521/pie.png?raw=true)

#### Articles per day

There seems to be a repeating pattern for the amount of articles that get published each day of the week. During the week appear more new articles than on weekends and the peak is around Friday.
On May 13th a lot less articles than expected were published, which is most likely due to it being a national holiday (Christi Himmelfahrt/Männertag).

![week](/_screenshots/0521/am_line.jpg?raw=true)

### Sentiment per Category

I wrote an AI that assigned each word in every category a sentiment score between -1 and 1. The mean of all individual scores per word resulted in a score for each article. This article score is an indicator for the overall positivity/negativity of an article.

- -1	very negative
-  0	neutral
-  1	very positive

The following graphic shows the sum of sentiments per category. An article with 0.5 Sentiment, and another one with -0.5 Sentiment would even each other out to 0. An article with 0.2 and one with -0.4 would result in -0.2.

![sent_cat](/_screenshots/0521/sent_sum.jpg?raw=true)

*Panorama* and *Ausland* are the only categories with negative sentiment. *Sport* articles are very positive and all other categories are overall positive.
Interestingly *Wirtschaft* and *Sport* have roughly the same amount of articles, but the Sentiment rating of *Sport* is about 4 times more positive than *Wirtschaft*

The graphic below displays the mean sentiment per category as a box plot. The least positive Article in *Tests* has a sentiment score of `0.32`, which is still in the top 26% of most positive rated articles.

![sent_test](/_screenshots/0521/sent_box.jpg?raw=true)
