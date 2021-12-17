<script src="https://cdn.plot.ly/plotly-2.6.3.min.js"></script>
# Introduction

## Abstract

**American newspapers** cover all kinds of topics from politics to sports, business, environment, etc... At the highest level, one could ask which topics people are mostly interviewed about. One way to answer this question is by trying to infer the theme each Quotebank citation is treating in an unsupervised manner and draw a distribution over some labels/classes representing these themes. Once all citations are classified with a certain confidence probability, a lower-level question could be: for each class, is it possible to relate the quotes’ frequency with some real world event? For instance, could an increase of citations about economics forecast some variation in the American stock market? In addition, using these classified quotes combined with additional data on the authors characteristics, we would like to compare the features of the authors of a particular citation class and try to find recurrent attributes or relevant features.

We will go trough a few question we asked ourselves : 
- **Who has the most space in the media?**
- **What subjects are treated the most?**
- **What are the common features of often-interviewed people?**

## Methods

In our data story, we chose to take only New York Times quotes because it represents the American newspapers well, and is a reasonable sample of our data and much easier to work with than with the massive original dataset. 
We will consider three main aspects:
- the **number of occurrences** of the quotes
- the **features** of the speakers
- the **economic topics** of the quotes

To analyse those aspects, we will use several techniques:
- **BERT topic** analysis to get the economic topics
- **PCA** to understand the link between the features of the speaker and the number of occurrences of his·her quotes
- Comparison of Doe Jones with the frequency of citations and compare this frequency with real world event’s timeline, as for the Dow Jones index.


# Who speaks the most? 

## Nationality
    
The distribution of the different **nationalities** of the speakers that are in the dataset is the following. It is grouped by the num of occurrences of the quotation, that is to say we counted a speaker X times if the quotation he·she is involved in appears X times. Almost the three quarters are american speakers. The main speakers come from America or Europe. The main ones correlate with the countries that have been awarded the price of "soft power" influence. As it can be seen in [wikipedia webpage](https://en.wikipedia.org/wiki/Soft_power), the last three different winners were: the **USA**, **United Kingdom** and **France**.

{% include_relative base__nationality_counting.html %}

## Gender

**Gender** equality is sadly far from being present our dataset. The distribution of the different genders of the speakers is the following. For the rest of the analysis, genders other than male and female will be gathered in a "other" category as there are a really few of them.

{% include_relative base__gender_counting.html %}

## Occupation

The distribution of the different **work occupations** of the speakers that are in the dataset is the following. It is grouped by the num of occurrences of the quotation, that is to say we counted a speaker X times if the quotation he·she is involved in appears X times. The split is more discrete but some work types stand out: almost of the quotes are told by specific jobs which are all related to publishing something to a public. It is not surprising that people who first publish work publicly and already have a sort of relationship with the population are the ones that are the most quoted. 

{% include_relative base_occupation_counting.html %}
  
# Do the specific combination of features of a speaker have a influence on the number of quotation?

A **PCA model** was trained on all the features of the speaker composed of:
- **date of birth**
- **nationality** which has been split in onehot vectors
- **gender** which has been split in onehot vectors
- **work occupation** which has been split in onehot vectors

It corresponds to a bit more than 2’000 columns (taking into account all the genders, all the nationalities and all the work occupation as well as the date of birth of the speaker). We didn't set any number of components as we wanted to study the global influence of the columns on the number of occurrences.

As one can see below, 50 columns are considered a bit more important that the others. It means that only 50 columns could be necessary to represent the number of occurrences of all quotations. However, the highest variance is only around 1%. 

{% include_relative pca_explained_var.html %}


# Let BERTopic tell us what are the quotes about.

{% include_relative topic_distribution.html %}
        
The above barplot shows the distribution over the 20 first topics that were given by our BERTopic model. We see that the relationship between the USA and Russia takes up a lot of space in the New York Times. In second place, we find China and it capital. These two first topics dominate all others by far. It looks like New York Times is fond of ambiguous international relationships... Now look how impressive BERTopic is at clustering the other topics!

In the two figures below, one can find the interdistance map of the first 500 topics and a hierarchical clusturing.
{% include_relative visualize_topic_500.html %}


{% include_relative visualize_hierarchy.html %}
# Let's focus now on economics topics: 
The selection of words related to economics has been done manually.
{% include_relative wordcloud.html %}
We could then automatically select economic topics among the BERTopic generated ones and finally have 3169 quotes characterised as "related to economics".

## Nationality
 
 The distribution of the different **nationalities** of the speakers that are talking about economy is the following. More than the three quarters are american speakers: American people are even more quoted when it concerns economy. The main speakers come from America or Europe. The main ones correlate with the countries that have been awarded the price of "soft power" influence. As it can be seen in [wikipedia webpage](https://en.wikipedia.org/wiki/Soft_power), the last three different winners were: the USA, France and United Kingdom.       
{% include_relative in_eco_topic_nationality_counting.html %}

## Gender
        
**Gender** inequality is a bit equivalent to when all the quotes were considered.

{% include_relative in_eco_topics_gender_counting.html %}

## Occupation

The distribution of the different **work occupations** of the speakers that are talking about economy is the following. The politician are 2 points more quoted when the economic quotes are considered. Furthermore, as before, more than half of the quotes are told by specific jobs which are all related to publishing something to a public.
        
{% include_relative in_eco_topics_occupation_counting.html %}
        
# Does it impact Economics ? 

{% include_relative dowjones1.html %}

        
Our next analysis consists in zooming into the domain of economics and trying to infer common variation between the quotation frequency and the Dow Jones Index which is the oldest price-weighted measurement stock market index in the United States. Feel free to zoom into the plot by selecting a window. It’s obvious that the year 2017 was very rich in economic quotes and it seems related to a massive increase of the Dow Jones. The reasons for this increase are beyond the scope of this study but could be interesting to investigate.
{% include_relative dowjones_vs_quotes_2015-01-01-2020-04-16_.html %}
    
# Conclusion
In this study, we had the chance to work on a brand new dataset freshly coming out of the DLAB at EPFL containing quotes from many English-speaking newspapers. The massive amount of available data led us to the choice of focusing our study on the New York Times only. We were able to make some statistics about the dataset augmented with some wikidata on the authors of the quotes. One of the challenges was to cluster the quotes into topics in an unsupervised manner using BERTopic library and training a model able to label the quotes with precise topics. 

