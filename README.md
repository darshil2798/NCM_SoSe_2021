# NCM_SoSe_2021

For the final project for the course NLP in Data Science University, the task chosen was to parse https://pubmed.ncbi.nlm.nih.gov/ and create a dataset of 10,000 abstracts.The dataset was created using the Entrez utility and following search terms.

a) Abstracts containing Drug adverse events
PubMed Query: "Drug-Related Side Effects and Adverse Reactions"[Mesh]
b) Abstracts containing Congenital anomalies
PubMed Query: "Congenital Abnormalities"[Mesh]
c) Abstracts containing both (a) and (b)
Cases where PMID from A and B overlap
d) Others
PubMed Query: NULL

Initial analysis suggested the "Both" class was undersampled compared to the rest of the dataset. This could be one of the reasons to impact model performance and it is suggested fixing the sample in future iterations by working with PubMed/MESH domain expert.

Before building any features, I cleaned and prepared the text data by removing special characters, etc.Since stemming can produce output words that don't exist, I'll only use a lemmatization process at this moment. Lemmatization takes into consideration the morphological analysis of the words and returns words that do exist, so it will be more useful for us.

After the initial preprocessing was done, I used TF-IDF vectorization to build features and defined the different parameters:

ngram_range: We want to consider both unigrams and bigrams.
max_df: When building the vocabulary ignore terms that have a document frequency strictly higher than the given threshold
min_df: When building the vocabulary ignore terms that have a document frequency strictly lower than the given threshold.
max_features: If not None, build a vocabulary that only consider the top max_features ordered by term frequency across the corpus.

It has to be mentioned that different combinations of these parameters could be tried in order to improve even more the accuracy of the models.

Please note that I have fitted and then transformed the training set, but we have only transformed the test set.

Three models were built to test performance; Random Forest, logistic regression and KNN. The test set accuracies of them were 0.78,0.77,0.74 respectively

Overall model performance is suboptimal. This is partly due to the difficulties encountered during the data creation stage of the analysis. Working with a PubMed/MESH content expert would help mitigate these issues which would hopefully improve model performance. In additon to working with domain experts, future iterations of model design should explore the following alternative methods of feature extraction (outlined above) and the inclusion of ommited algorithms such as Gradient Boosting.
