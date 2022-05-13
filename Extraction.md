## Document Overview
This document specifies the methodologies that I took to extract twitter text data into structured data. 
For the extraction, I used a python module called `twint`, which were developed to extract posted twitter text data along with its meta data such as username, date, language ...etc.
This twitter scraper allows for in-depth extraction of tweets without the need for official API, which is not free. As a college student, this was the best way to go.

## Module Import
```python
import twint #https://github.com/twintproject/twint
import nest_asyncio
import pandas as pd
import timeit
nest_asyncio.apply()
```

## Tweet Extraction
```python
#Initialize search list.
search_list = ['neuralink', 'machine brain interface']
start = timeit.default_timer()
for keyword in search_list:
    # Configure.
    c = twint.Config()
    c.Search = keyword
    c.Store_json = True
    c.Output = "/Users/takucnoelendo/Documents/Machine Learning/Tweet Mining/Data/nuralinktweet.json"
    # Run
    twint.run.Search(c)
stop = timeit.default_timer()
print('Runtime:', stop-start)
```
## Data Storage and Exportation
```python
#Read json file into pandas dataframe.
data = pd.read_json("/Users/takucnoelendo/Documents/Machine Learning/Tweet Mining/Data/nuralinktweet.json", \
                    lines=True)
data.to_csv('/Users/takucnoelendo/Documents/Machine Learning/Tweet Mining/Data/nuralinktweet.csv', index=False)
```
