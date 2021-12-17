<script src="https://cdn.plot.ly/plotly-2.6.3.min.js"></script>
# A hierarchical study of American newspaper: Focus on New York Times

## Introduction

Newspapers’ role in society is to inform the public of all sorts of topics, give people a voice to publicly show their opinion. When looking at the persons that are quoted in the newspapers, one could ask whether some characteristics like gender or nationality could increase the likelihood to be given a public voice. In parallel, one could want to know which topics are reviewed the most, and see if there are similarities or differences between speakers for all quotes and speakers from a particular topic. 

We will go trough a few question we asked ourselves : 
- Who has the most space in the media? 
- What subjects are treated the most? 

### Who speaks the most? 
<div markdown="0">
    <div id="1">
    </div>
    <style>
    
@property --num {
  syntax: "<integer>";
  initial-value: 0;
  inherits: false;
}

div#1 {
  animation: counter 5s infinite alternate ease-in-out;
  counter-reset: num var(--num);
  font: 800 40px system-ui;
  padding: 2rem;
}
div#1::after {
  content: counter(num)+"%";
}

@keyframes counter {
  from {
    --num: 0;
  }
  to {
    --num: 100;
  }
}
    </style
</div>
    
The distribution of the different speakers that are in our dataset is the following. It is grouped by the num of occurrences of the quotation, that is to say we counted a speaker X times if the quotation he·she is involved in appears X times. We found out that almost the three quarters are american speakers. The main speakers come from America or Europe. The main ones correlate with the countries that have been awarded the price of "soft power" influence. As it can be seen in [wikipedia webpage](https://en.wikipedia.org/wiki/Soft_power), the last three different winners were: the USA, France and United Kingdom.

{% include_relative base__nationality_counting.html %}

Gender equality is sadly far from our dataset. The distribution of the different genders is the following. For the rest of the analysis, we will gather the genders other than male and female in a "other" category as there are a really few of them.
{% include_relative base__gender_counting.html %}


{% include_relative base_occupation_counting.html %}
        
        #### mettre barplot topic
The above barplot shows the distribution over the 20 first topics that were given by our BERTopic model. We see that the relationship between the USA and Russia takes up a lot of space in the New York Times. In second place, we find China and it capital. These two first topics dominate all others by far. It looks like New York Times is fond of ambiguous international relationships... Now look how impressive BERTopic is at clustering the other topics!
        
## Let's concentrate on economics topics : 
We've started by manually selecting some words related to economics.
{% include_relative wordcloud.html %}
We could then automatically select economic topics among the BERTopic generated ones and finally have XXX quotes characterised as "related to economics".
      
 
{% include_relative in_eco_topic_nationality_counting.html %}

{% include_relative in_eco_topics_gender_counting.html %}
 Gender inequality is very high in this fields !

 
{% include_relative in_eco_topics_occupation_counting.html %}
        
### Does it impact Economics ? 

{% include_relative dowjones1.html %}

        
    Our next analysis consists in zooming into the domain of economics and trying to infer common variation between the quotation frequency and the Dow Jones Index which is the oldest price-weighted measurement stock market index in the United States. Feel free to zoom into the plot by selecting a window. It’s obvious that the year 2017 was very rich in economic quotes and it seems related to a massive increase of the Dow Jones. The reasons for this increase are beyond the scope of this study but could be interesting to investigate.
{% include_relative dowjones_vs_quotes_2015-01-01-2020-04-16_.html %}
    
