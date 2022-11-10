---
layout: page
title: Chronicling America API Assignment
description: Learn about API
---
# Chronicling America API Assignment
In this assignment, you are tasked with:
* searching Chronicling America's API for a key word of your choice
* parsing your results from a dictionary to a `DataFrame` with headings "title", "city", 'date", and "raw_text"
* processing the raw text by removing "\n" characters, stopwords, and then lemmatizing the raw text before adding it to a new column called "lemmas."
* saving your `DataFrame` to a csv file

If you need any help with this assignment please email micah.saxton@tufts.edu



```python
# imports
import requests
import json
import math
import pandas as pd
import spacy
```

searching the key_word: disney from year 1920 to 1963


```python
# initial search
# searching the key_word: disney from year 1920 to 1963
url = 'https://chroniclingamerica.loc.gov/search/pages/results/?state=&date1=1945&date2=1963&proxtext=Industrialization&x=16&y=8&dateFilterType=yearRange&rows=20&searchType=basic&format=json'
response = requests.get(url)  # returns a 'object' representing the webpage
raw = response.text  # the text attribute contains the text from the web page as a string
results = json.loads(raw)  # the loads method from the json library transforms the string into a dict

```


```python
# find total amount of pages
total_pages = math.ceil(results['totalItems']/results['itemsPerPage'])
print(total_pages)
```

    12169



```python
# query the api and save to dict 
data = []
start_date = '1945'
end_date = '1963'
search_term = 'Industrialization'
for i in range(1, 6):  
    url = (f'https://chroniclingamerica.loc.gov/search/pages/results/?state=&date1={start_date}'
           f'&date2={end_date}&proxtext={search_term}&x=16&y=8&dateFilterType=yearRange&rows=20'
           f'&searchType=basic&format=json&page={i}')  # f-string
    response = requests.get(url)
    raw = response.text
    print(response.status_code)  # checking for errors
    results = json.loads(raw)
    items_ = results['items']
    for item_ in items_:
        temp_dict = {}
        temp_dict['title'] = item_['title_normal']
        temp_dict['city'] = item_['city']
        temp_dict['date'] = item_['date']
        temp_dict['raw_text'] = item_['ocr_eng']
        data.append(temp_dict)
```

    200
    200
    200
    200
    200



```python
with open('../data/backup-data.json', 'w') as f:
   json.dump(data, f)
with open('../data/backup-data.json', 'r') as f:
   data = json.load(f)
```


```python
# convert dict to dataframe
df = pd.DataFrame.from_dict(data)
df.head()
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
      <th>title</th>
      <th>city</th>
      <th>date</th>
      <th>raw_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>evening star.</td>
      <td>[Washington]</td>
      <td>19560803</td>
      <td>3.4 Million Population\nSeen for Area in 1980\...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>evening star.</td>
      <td>[Washington]</td>
      <td>19480831</td>
      <td>!* ” «-•\nMake Perfect Iced Tea\nMake tea Cj? ...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>daily express.</td>
      <td>[Dayton]</td>
      <td>19510120</td>
      <td>^~eminine ^~adhion 3L\nHello Firends: Just lik...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>chapel hill weekly.</td>
      <td>[Chapel Hill]</td>
      <td>19630721</td>
      <td>Page 2\nWhat Bait For Industry?\nBy NANCY VON ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chapel hill weekly.</td>
      <td>[Chapel Hill]</td>
      <td>19630602</td>
      <td>Sunday, June 2,1963\nSouthern Business Leaders...</td>
    </tr>
  </tbody>
</table>
</div>




```python
# convert date column from string to date-time object
df['date'] = pd.to_datetime(df['date'])
```


```python
# sort by date
sorted_df = df.sort_values(by='date')
sorted_df.head()
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
      <th>title</th>
      <th>city</th>
      <th>date</th>
      <th>raw_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>65</th>
      <td>automotive news.</td>
      <td>[Detroit]</td>
      <td>1945-04-02</td>
      <td>12\nKeller Urges\nPreparedness in\nArms Know-H...</td>
    </tr>
    <tr>
      <th>96</th>
      <td>daily bulletin.</td>
      <td>[Dayton]</td>
      <td>1945-04-26</td>
      <td>U Page 6\nBuy War Bonds\nKflfiTs\n10 DAY SERVI...</td>
    </tr>
    <tr>
      <th>57</th>
      <td>evening star.</td>
      <td>[Washington]</td>
      <td>1945-05-06</td>
      <td>« BLACK STAB\nCRAMPED: The East boasts too muc...</td>
    </tr>
    <tr>
      <th>58</th>
      <td>automotive news.</td>
      <td>[Detroit]</td>
      <td>1945-05-28</td>
      <td>18\nKy. Plan Hoard\nHits Labor Grab\nFor Manag...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>daily bulletin.</td>
      <td>[Dayton]</td>
      <td>1945-06-20</td>
      <td>FAIR\nFEARLESS\nThe\nEy Ernest E. Johnson\nWAS...</td>
    </tr>
  </tbody>
</table>
</div>




```python
# write fuction to process text
nlp = spacy.load("en_core_web_sm")
nlp.disable_pipes('ner', 'parser')  # these are unnecessary for the task at hand

def process_text(text):
    """Remove new line characters and lemmatize text. Returns string of lemmas"""
    text = text.replace('\n', ' ')
    doc = nlp(text)
    tokens = [token for token in doc]
    no_stops = [token for token in tokens if not token.is_stop]
    no_punct = [token for token in no_stops if token.is_alpha]
    lemmas = [token.lemma_ for token in no_punct]
    lemmas_lower = [lemma.lower() for lemma in lemmas]
    lemmas_string = ' '.join(lemmas_lower)
    return lemmas_string
```


```python
# apply process_text function to raw_text column
sorted_df['lemmas'] = sorted_df['raw_text'].apply(process_text)
```


```python
sorted_df.head()
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
      <th>title</th>
      <th>city</th>
      <th>date</th>
      <th>raw_text</th>
      <th>lemmas</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>65</th>
      <td>automotive news.</td>
      <td>[Detroit]</td>
      <td>1945-04-02</td>
      <td>12\nKeller Urges\nPreparedness in\nArms Know-H...</td>
      <td>keller urges preparedness arms know aberdeen p...</td>
    </tr>
    <tr>
      <th>96</th>
      <td>daily bulletin.</td>
      <td>[Dayton]</td>
      <td>1945-04-26</td>
      <td>U Page 6\nBuy War Bonds\nKflfiTs\n10 DAY SERVI...</td>
      <td>u page buy war bonds kflfits day service makes...</td>
    </tr>
    <tr>
      <th>57</th>
      <td>evening star.</td>
      <td>[Washington]</td>
      <td>1945-05-06</td>
      <td>« BLACK STAB\nCRAMPED: The East boasts too muc...</td>
      <td>black stab cramped east boast man marvel weste...</td>
    </tr>
    <tr>
      <th>58</th>
      <td>automotive news.</td>
      <td>[Detroit]</td>
      <td>1945-05-28</td>
      <td>18\nKy. Plan Hoard\nHits Labor Grab\nFor Manag...</td>
      <td>plan hoard hit labor grab management frankfort...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>daily bulletin.</td>
      <td>[Dayton]</td>
      <td>1945-06-20</td>
      <td>FAIR\nFEARLESS\nThe\nEy Ernest E. Johnson\nWAS...</td>
      <td>fair fearless ey ernest johnson washington anp...</td>
    </tr>
  </tbody>
</table>
</div>




```python
# save to csv
sorted_df.to_csv(f'../data/{search_term}{start_date}-{end_date}.csv',index=False)
```
