# Elasticsearch-API-exploratory Python


Your task
This task comes in stages. Marks are given for each stage. The stages are as follows:
•	Indexing (20%) The first step for you will be to obtain the dataset. Once you have done so upload a sample of 1000 articles with full text to Elasticsearch (the simplest thing is to use the first 1000 documents). 
•	Sentence Splitting, Tokenization and Normalization (10%) The next step should be to transform the input text into a normal form of your choice. This should include the identification of sentences, bullet points and cells in tables.
•	Selecting Keywords (20%) One aim of your system is to identify the words and phrases in the text that are most useful for indexing purposes. Your system should remove words which are not “useful”. E.g. very frequent words or stopwords. You should also identify phrases suitable as index terms. Apply tf.idf as part of your selection and weighting step.
•	Stemming or Morphological Analysis (10%) Writing word stems to the database rather than words allows to treat various inflected forms of a word in the same way, e.g. bus and busses refer to exactly the same thing even though they are different words.
•	Searching (10%) Once you have indexed the collection you want to be able to search it. You can do that on the command line, but it would be much better to have an interactive system. You could start with Kibana for that but you are free to use other open source tools for your Graphical User Interface (GUI). Note that the each article in the collection contains different fields. Make sure that a user can decide which field to search (Hint: one of the fields is the Release Year).

•	Engineering a Complete System (10%) The final system should allow a user to have control over all the individual components, so in the final result we will have a complete search engine, not disperate code.
