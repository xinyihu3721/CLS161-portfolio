---
layout: page
title: Sentiment Analysis for exploratory data analysis
description: This lesson uses Python to apply sentimental analysis on email-correspondence.
---
## Source ##
[Saldaña, Z. W. (2018, January 15). Sentiment Analysis for exploratory data analysis. Programming Historian. Retrieved October 7, 2022. https://doi.org/10.46430/phen0079](https://programminghistorian.org/en/lessons/sentiment-analysis) 

## Reflection ##
This lesson is about how to use Natural Language Processing techniques to analyze and acquire sentimental components of text pieces. The sentimental analysis belongs to the analyses category. According to the article, "**Exploratory data analyses** are strategies that summarize or otherwise reveal features of interest within a dataset which are not likely visible through traditional close reading".  NLP approaches can help researchers to explore their textual data and discover clues or indications that might be worth further investigation. In this notebook, we analyzed email transcripts from the bankrupt American energy company Enron, and we investigated why the component value of the sentimental analysis might not be able to grasp the actual sentiments conveyed in the correspondence.  

We used the NLTK to generate sentiment scores from e-mail transcripts. After running the NLTK model on our text, the output is a dictionary with four `keys`: 'pos', 'neg', 'neu', and 'compound'. The 'pos', 'neg', and 'neu' means the positive, negative, and neutral components of the text. And compound calculates the combined score of the three.  The“compound” value is normalized between -1 and 1; it attempts to describe the overall effect of the entire text from strongly negative (-1) to strongly positive (1).

Sentimental analysis can be used to study the transitioning of emotional affect in a literature narrative. 
## Code ##


```python
import nltk
nltk.download('vader_lexicon')
nltk.download('punkt')
```

    [nltk_data] Downloading package vader_lexicon to
    [nltk_data]     /Users/selenahu/nltk_data...
    [nltk_data]   Package vader_lexicon is already up-to-date!
    [nltk_data] Downloading package punkt to /Users/selenahu/nltk_data...
    [nltk_data]   Package punkt is already up-to-date!





    True




```python
from nltk.sentiment.vader import SentimentIntensityAnalyzer
#initialize VADER
sid =  SentimentIntensityAnalyzer()
```


```python
#import message
message_text = '''Like you, I am getting very frustrated with this process. I am genuinely trying to be as reasonable as possible. I am not trying to "hold up" the deal at the last minute. I'm afraid that I am being asked to take a fairly large leap of faith after this company (I don't mean the two of you -- I mean Enron) has screwed me and the people who work for me.'''
print(message_text)
```

    Like you, I am getting very frustrated with this process. I am genuinely trying to be as reasonable as possible. I am not trying to "hold up" the deal at the last minute. I'm afraid that I am being asked to take a fairly large leap of faith after this company (I don't mean the two of you -- I mean Enron) has screwed me and the people who work for me.



```python
# run function
scores = sid.polarity_scores(message_text)
for key in sorted(scores):
        print('{0}: {1}, '.format(key, scores[key]), end='')
```

    compound: -0.3804, neg: 0.093, neu: 0.836, pos: 0.071, 

### more texts ###


```python
message_text1 = "Looks great.  I think we should have a least 1 or 2 real time traders in Calgary."
message_text2 = '''I think we are making great progress on the systems side.  I would like to
set a deadline of November 10th to have a plan on all North American projects
(I'm ok if fundementals groups are excluded) that is signed off on by
commercial, Sally's world, and Beth's world.  When I say signed off I mean
that I want signitures on a piece of paper that everyone is onside with the
plan for each project.  If you don't agree don't sign. If certain projects
(ie. the gas plan) are not done yet then lay out a timeframe that the plan
will be complete.  I want much more in the way of specifics about objectives
and timeframe.

Thanks for everyone's hard work on this.'''
```


```python
scores1 = sid.polarity_scores(message_text1)
scores2 = sid.polarity_scores(message_text2)
for key in sorted(scores1):
        print('{0}: {1}, '.format(key, scores1[key]), end='')
for key in sorted(scores2):
        print('{0}: {1}, '.format(key, scores2[key]), end='')
```

    compound: 0.6249, neg: 0.0, neu: 0.745, pos: 0.255, compound: 0.8951, neg: 0.042, neu: 0.821, pos: 0.136, 

The reuslt sentiments might not be accurate sometimes.


```python
message_text3 = '''It seems to me we are in the middle of no man's land with respect to the  following:  Opec production speculation, Mid east crisis and renewed  tensions, US elections and what looks like a slowing economy (?), and no real weather anywhere in the world. I think it would be most prudent to play  the markets from a very flat price position and try to day trade more aggressively. I have no intentions of outguessing Mr. Greenspan, the US. electorate, the Opec ministers and their new important roles, The Israeli and Palestinian leaders, and somewhat importantly, Mother Nature.  Given that, and that we cannot afford to lose any more money, and that Var seems to be a problem, let's be as flat as possible. I'm ok with spread risk  (not front to backs, but commodity spreads). The morning meetings are not inspiring, and I don't have a real feel for  everyone's passion with respect to the markets.  As such, I'd like to ask  John N. to run the morning meetings on Mon. and Wed.  Thanks. Jeff'''
scores3 = sid.polarity_scores(message_text3)
for key in sorted(scores3):
        print('{0}: {1}, '.format(key, scores3[key]), end='')
```

    compound: 0.889, neg: 0.096, neu: 0.765, pos: 0.14, 

### Sentimental analysis on each sentence
We split a long paragraph into sentences and then run analyze on each sentence.


```python
import nltk.data
from nltk import sentiment
from nltk import word_tokenize
tokenizer = nltk.data.load('tokenizers/punkt/english.pickle')
sentences = tokenizer.tokenize(message_text3)

for sentence in sentences:
        print(sentence)
        scores = sid.polarity_scores(sentence)
        for key in sorted(scores):
                print('{0}: {1}, '.format(key, scores[key]), end='')
        print()
```

    It seems to me we are in the middle of no man's land with respect to the  following:  Opec production speculation, Mid east crisis and renewed  tensions, US elections and what looks like a slowing economy (?
    compound: -0.5267, neg: 0.197, neu: 0.68, pos: 0.123, 
    ), and no real weather anywhere in the world.
    compound: -0.296, neg: 0.216, neu: 0.784, pos: 0.0, 
    I think it would be most prudent to play  the markets from a very flat price position and try to day trade more aggressively.
    compound: 0.0183, neg: 0.103, neu: 0.792, pos: 0.105, 
    I have no intentions of outguessing Mr. Greenspan, the US.
    compound: -0.296, neg: 0.216, neu: 0.784, pos: 0.0, 
    electorate, the Opec ministers and their new important roles, The Israeli and Palestinian leaders, and somewhat importantly, Mother Nature.
    compound: 0.4228, neg: 0.0, neu: 0.817, pos: 0.183, 
    Given that, and that we cannot afford to lose any more money, and that Var seems to be a problem, let's be as flat as possible.
    compound: -0.1134, neg: 0.097, neu: 0.823, pos: 0.081, 
    I'm ok with spread risk  (not front to backs, but commodity spreads).
    compound: -0.0129, neg: 0.2, neu: 0.679, pos: 0.121, 
    The morning meetings are not inspiring, and I don't have a real feel for  everyone's passion with respect to the markets.
    compound: 0.5815, neg: 0.095, neu: 0.655, pos: 0.25, 
    As such, I'd like to ask  John N. to run the morning meetings on Mon.
    compound: 0.3612, neg: 0.0, neu: 0.848, pos: 0.152, 
    and Wed.
    compound: 0.0, neg: 0.0, neu: 1.0, pos: 0.0, 
    Thanks.
    compound: 0.4404, neg: 0.0, neu: 0.0, pos: 1.0, 
    Jeff
    compound: 0.0, neg: 0.0, neu: 1.0, pos: 0.0, 

