# Elasticsearch-API-exploratory Python
---

### The stages are as follows:

#### Intrucstions for windows: 
The first step to start our system was to install Elasticsearch 7.16.3 in python by using: __!pip install elasticsearch==7.16.3__. Then, the second step is to run in the background Elasticsearch (same version). After Elasticsearch is running effectively in the background you can initiate elasticsearch in python with __es = Elasticsearch("http://localhost:9200")__.

As I am running my program in Windows is necessary go back to the elasticsearch folder on your pc then open the config folder, select the file __elasticsearch.yml__ and open it with notepad then look for “network.host:” and change the default __192.168.1.1__ for __localhost__ and you and ready to go.

#### •	Indexing:
The first step will be to obtain the dataset from [kaggle](https://www.kaggle.com/jrobischon/wikipedia-movie-plots?select=wiki_movie_plots_deduped.csv ). Then was uploaded a sample of 1000 articles with full text to Elasticsearch (the simplest thing is to use the first 1000 documents.

Second step was to remove the instances in the sample that contain missing values as they will affect the overall accuracy of the system. They were eliminated  using dropna() and now our instances were of 980.

The third step was to convert the updated sample into JSON as elasticsearch work naturally better with JSON files.

#### •	Sentence Splitting, Tokenization and Normalization: 
The next step should be to transform the input text into a normal form of your choice. This should include the identification of sentences, bullet points and cells in tables. 

Used:
```
"chard_filter": "html_strip"
"filter": ["lowercase", "word_delimiter"]
"tokenizer": "standard"
```

#### •	Selecting Keywords: 
One aim of your system is to identify the words and phrases in the text that are most useful for indexing purposes. So the best approach is to remove words which are not “useful”. E.g. very frequent words or stopwords. Also will be a good to get a great score for your search applying tf.idf.

Used:
```
"filter": 
    "type": "stop", 
    "stopwords": "_english_"
"similarity": "BM25"
```

#### •	Stemming or Morphological Analysis: 
Writing word stems to the database rather than words allows to treat various inflected forms of a word in the same way, e.g. bus and busses refer to exactly the same thing even though they are different words. Here was used Ngrams which are a great way to autocomplete your search.

Used:
```
"tokenizer__": 
     "type": "edge_ngram", 
     "min_gram": 2, 
     "max_gram":10,
     "token_chars":["letter","digit"]
```
---
## References
Elasticsearch guide [8.0](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)
W. Bruce Croft; Donald Metzler; Trevor Strohman. 2010. Search engines: information retrieval in practice. [Pearson Education.](http://ciir.cs.umass.edu/downloads/SEIRiP.pdf) 
