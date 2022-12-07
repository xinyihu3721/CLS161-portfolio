---
layout: page
title: TEI Assignment
description: Learn about TEI
---
# Parsing a TEI Document - Assignment

## Instructions

1. Parse the tei text of Gibbon's _Decline and Fall_ as found in `gibbon.xml`.
2. Extract all the footnotes and remove extraneous white space.
3. Place footnotes in a dataframe.
4. Save the dataframe as a csv file.

## Parsing TEI


```python
# imports
from bs4 import BeautifulSoup
import re
import pandas as pd
```


```python
# load xml file
with open('gibbon.xml', encoding='utf8', mode='r') as f:
    tei_string = f.read()
```


```python
# use BeatifulSoup to instntiate tei object
tei_object = BeautifulSoup(tei_string)
```


```python
# find all margin notes
margin_notes = tei_object.find_all('note', attrs={'place': 'bottom'})
```


```python
# clean margin notes and add to a list
clean_margin_notes = []
for margin_note in margin_notes:
    margin_note = re.sub(r'[\ \n]{2,}', '', margin_note.text) 
    margin_note = margin_note.replace('\n','')
    #margin_note = re.sub(r'[\n]{2,}', '', margin_note.text)# remove excess space
    clean_margin_notes.append(margin_note)
```


```python
# convert list to dataframe
margin_notes_df = pd.DataFrame(clean_margin_notes)
```


```python
# check dataframe
margin_notes_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pons Aureoli,thirteen miles from Bergamo, and ...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>On the death of Gallienus, ſee Trebellius Poll...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Some ſuppoſed him, oddly enough, to be a baſta...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Notoria,a periodical and official diſpatch whi...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Hiſt. Auguſt. p. 208. Gallienus deſcribes the ...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>823</th>
      <td>Euſebius de Martyr. Paleſtin. c. 13. He cloſes...</td>
    </tr>
    <tr>
      <th>824</th>
      <td>When Paleſtine was divided into three, the pra...</td>
    </tr>
    <tr>
      <th>825</th>
      <td>Ut gloriari poſſint nullum ſe innocentium pere...</td>
    </tr>
    <tr>
      <th>826</th>
      <td>Grot. Annal. de Rebus Belgicis, l. i. p. 12. E...</td>
    </tr>
    <tr>
      <th>827</th>
      <td>Fra-Paolo (Iſtoria del Concilio Tridentino, l....</td>
    </tr>
  </tbody>
</table>
<p>828 rows × 1 columns</p>
</div>




```python
# save datafram as csv
margin_notes_df.to_csv('foot_notes.csv')
```
