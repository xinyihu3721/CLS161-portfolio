---
layout: post
title:  "NLP & API "
date:   "2022-10-13"
categories: jekyll update
---
## Introduction to Named Entity Recognition ##

We have two readings for this week, *Introduction to Named Entity Recognition*, which introduces Natural Language Processing and Named Entity recognition. NLP is the general name for a type of textual analysis method. For example, NER and sentimental analysis are both under the hood of NLP. While sentimental analysis tries to measure the underlying sentiments in a text, NER helps researchers to extract different types of entities from the text. To be more precise, NER can help to identify and extract information that is related to dates, events, names, behaviors, etc.   

It is important to notice the drawbacks of some NLP packages and models such as the NER model in spaCy. Most of those models are trained under a general context, which might not be suitable for some specialized areas, such as law and classical literature. In those specialized areas, the alternative method could be training a new model specifically for the focused area. Since I never trained a model before, **I really want to know what the model has learned from the texts (i.e., data format? vectors?) and how do we transfer such a learned model to another device or system? Is it always better to give the model as much information as possible? How do we make sure that we are not overfitting the model, and what are some checking criteria? **  
## Getting Data for Digital Humanities with APIs: ##
### A Gentle Introduction ###
The second reading *Getting Data for Digital Humanities with APIs*is very technical about API extraction. This paper emphasized how we can use API to extract text and information online from other libraries and databases. However, it is not mentioned in the reading about how to implement an API (can we use API from python?). Sometimes API also functions in the way that we can use the API to run some algorithms.  For example, the google map API can give us directions after we send the starting point and the destination to the API. Usually, API will return data written in JSON format. The following question after data extraction from API might be how do we parse information from a JSON file? Suppose it is unavoidable to use API, one has to learn how to parse and loop through JSON files.   