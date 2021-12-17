<script src="https://cdn.plot.ly/plotly-2.6.3.min.js"></script>
# A hierarchical study of American newspaper quotes and speaker characteristics

## Introduction

Newspapers’ role in society is to inform the public of all sorts of topics, give people a voice to publicly show their opinion. When looking at the people that are quoted in the newspapers, one could ask whether some characteristics like gender or nationality could increase the likelihood to be given a public voice. In parallel, one could  want to know which topics are reviewed the most, and see if there are similarities or differences between speakers for all quotes and speakers from a particular topic. 

We will go trough a few question we asked ourselves : 
- Who has the most space in the media? 
- What subjects are treated the most? 

### Who speaks the most ? 
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
}</style
</div>
    
Behind this, we found out that a lot of speakers a not americans 
 
### Does it impact Economics ? 

{% include_relative dowjones1.html %}

{% include_relative dowjones_vs_quotes_2015-01-01-2020-04-16_.html %}
    
