**Extracting Comments from Twitter on a Specified Topic using Python**

**By: -**

**Team Name - MCXXX**

**Sai Krishna Kanth VS (21BLC1211) 
` `Vedant Shah (21BCE5111)**

**Introduction:**

Social media platforms like Twitter serve as a treasure trove of valuable information, including public opinions and discussions on various topics. Extracting comments from Twitter without using the official Twitter API can be challenging, but it is possible using web scraping techniques. In this report, we present a Python-based approach to extract comments from Twitter on a specified topic.

**Code:**

import pandas as pd

from tqdm.notebook import tqdm

from ntscraper import Nitter

def Get\_Tweets(name,modes,limit):

`    `scraper = Nitter()

`    `tweets= scraper.get\_tweets(name,mode=modes,number=limit)

`    `final\_tweets = []

`    `for x in tweets['tweets']:

`        `data = [x['link'],x['date'],x['user']['name'],x['text'],x['is-retweet'],x['stats']['likes'],x['stats']['comments']]

`        `final\_tweets.append(data)

`    `data = pd.DataFrame(final\_tweets, columns =['Link','Date','Name','Tweet','Retweet','Likes','Comments'])

`    `data.to\_csv("{}\_Twitter.csv".format(name),index=False,encoding='utf-8')

print("=======================================")

name=input("Enter Term to Extract Tweets: ")

limit=int(input("Enter no of tweets: "))

print("Word Type-\n1. Username\n2. Hashtag\n3. Term")

modes=int(input("Enter Type No: "))

print("=======================================")

if modes==1:

`    `mode="user"

`    `Get\_Tweets(name,mode,limit)

elif modes==2:

`    `mode="hashtag"

`    `Get\_Tweets(name,mode,limit)

elif modes==3:

`    `mode="term"

`    `Get\_Tweets(name,mode,limit)

**Output:**

\```

![](Aspose.Words.c7516059-aada-4a64-a7d3-bc913b7b22d0.001.png)

\```

**Conclusion:**

While extracting comments from Twitter without using the Twitter API is feasible, it comes with certain limitations. Web scraping may violate the terms of service of the platform, and the structure of the HTML may change, affecting the script's reliability. Additionally, web scraping may lead to rate limiting or temporary IP bans.

It's important to note that using the official Twitter API is the recommended and ethical way to access Twitter data programmatically. However, in cases where API access is restricted or unavailable, the presented Python script provides a basic example of how comments can be extracted from Twitter using web scraping techniques.

Developers should exercise caution, respect ethical guidelines, and be aware of potential legal implications when employing web scraping methods for data extraction from online platforms. Additionally, regular updates and adjustments to the script may be necessary to adapt to changes in the Twitter website's structure.

