<script src="https://cdn.plot.ly/plotly-2.6.3.min.js"></script>
# A hierarchical study of American newspaper: Focus on New York Times

## Introduction

Newspapers’ role in society is to inform the public of all sorts of topics, give people a voice to publicly show their opinion. When looking at the persons that are quoted in the newspapers, one could ask whether some characteristics like gender or nationality could increase the likelihood to be given a public voice. In parallel, one could want to know which topics are reviewed the most, and see if there are similarities or differences between speakers for all quotes and speakers from a particular topic. 

We will go trough a few question we asked ourselves : 
- Who has the most space in the media? 
- What subjects are treated the most? 

### Who speaks the most? 
    
The distribution of the different nationalities of the speakers that are in the dataset is the following. It is grouped by the num of occurrences of the quotation, that is to say we counted a speaker X times if the quotation he·she is involved in appears X times. Almost the three quarters are american speakers. The main speakers come from America or Europe. The main ones correlate with the countries that have been awarded the price of "soft power" influence. As it can be seen in [wikipedia webpage](https://en.wikipedia.org/wiki/Soft_power), the last three different winners were: the USA, France and United Kingdom.

{% include_relative base__nationality_counting.html %}

Gender equality is sadly far from our dataset. The distribution of the different genders of the speakers is the following. For the rest of the analysis, genders other than male and female will be gathered in a "other" category as there are a really few of them.

{% include_relative base__gender_counting.html %}

The distribution of the different work occupations of the speakers that are in the dataset is the following. It is grouped by the num of occurrences of the quotation, that is to say we counted a speaker X times if the quotation he·she is involved in appears X times. The split is more discrete but some work types stand out: almost of the quotes are told by specific jobs which are all related to publishing something to a public. It is not surprising that people who first publish work publicly and already have a sort of relationship with the population are the ones that are the most quoted. 

{% include_relative base_occupation_counting.html %}
        

{% include_relative topic_distribution.html %}
        
The above barplot shows the distribution over the 20 first topics that were given by our BERTopic model. We see that the relationship between the USA and Russia takes up a lot of space in the New York Times. In second place, we find China and it capital. These two first topics dominate all others by far. It looks like New York Times is fond of ambiguous international relationships... Now look how impressive BERTopic is at clustering the other topics!
{% include_relative visualize_topic_200.html %}
{% include_relative visualize_hierarchy.html %}
## Let's focus now on economics topics: 
The selection of words related to economics has been done manually.
{% include_relative wordcloud.html %}
We could then automatically select economic topics among the BERTopic generated ones and finally have XXX quotes characterised as "related to economics".
      
 
 The distribution of the different nationalities of the speakers that are talking about economy is the following. More than the three quarters are american speakers: American people are even more quoted when it concerns economy. The main speakers come from America or Europe. The main ones correlate with the countries that have been awarded the price of "soft power" influence. As it can be seen in [wikipedia webpage](https://en.wikipedia.org/wiki/Soft_power), the last three different winners were: the USA, France and United Kingdom.       
{% include_relative in_eco_topic_nationality_counting.html %}

        
Gender inequality is a bit equivalent to when all the quotes were considered.

{% include_relative in_eco_topics_gender_counting.html %}


The distribution of the different work occupations of the speakers that are talking about economy is the following. The politician are 2 points more quoted when the economic quotes are considered. Furthermore, as before, more than half of the quotes are told by specific jobs which are all related to publishing something to a public.
        
{% include_relative in_eco_topics_occupation_counting.html %}
        
### Does it impact Economics ? 

{% include_relative dowjones1.html %}

        
    Our next analysis consists in zooming into the domain of economics and trying to infer common variation between the quotation frequency and the Dow Jones Index which is the oldest price-weighted measurement stock market index in the United States. Feel free to zoom into the plot by selecting a window. It’s obvious that the year 2017 was very rich in economic quotes and it seems related to a massive increase of the Dow Jones. The reasons for this increase are beyond the scope of this study but could be interesting to investigate.
{% include_relative dowjones_vs_quotes_2015-01-01-2020-04-16_.html %}
    
