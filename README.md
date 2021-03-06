# Topic modelling

## Overview

Unsupervised. NLP. Topic modelling is a clustering method in which you identify the type of document based on specific sets of keywords of that document. 
You can see it as document/text/message classification but you do not have access to predefined set of labels.
The term ‘topic’ refers to a set of words that come to mind when we think of a topic.
For instance, when we think of ‘entertainment’- the topic, the words that come to the mind are ‘movies’, ‘sitcoms’, ‘web series’, ‘Netflix’, ‘YouTube’ and so on

Underlying assumptions in topic modelling; 
1. The distributional assumption indicates that similar topics make use of similar words.
2. The statistical mixture assumption indicates that each document deals with several topics. 

Simply put, for a given corpus of documents, each document can be represented as a 
statistical distribution of a fixed set of topics. 
The role of the topic model is to identify the topics and represent each document as a distribution of these topics. 


## Latent Dirichlet Allocation

LDA is a popular topic modelling technique. The word **‘Latent’** indicates that the model discovers the ‘yet-to-be-found’ 
or hidden topics from the documents. **‘Dirichlet’** indicates LDA’s assumption that the distribution of topics in a document 
and the distribution of words in topics are both Dirichlet distributions. **‘Allocation’** indicates the distribution of topics in the document.  

Dirichlet is a type of distribution specified by a vector parameter containing variables corresponding
to each topic. LDA formula : probability of a topic given a word = # of times topic in document * # of times word is in the topic

P(z=t|w) &prop; (&alpha;<sub>t</sub> + n<sub>t|d</sub>) * (&beta; + n<sub>w|d</sub>) / (&beta;V + n<sub>.|t</sub> )

with V the number of words in vocabulary, &alpha; the document-topic density factor, &beta; the topic-word density factor

## Topic modelling vs topic classification

At this point, it is important to note that topic modelling is not the same as topic classification. 
Topic classification is a supervised learning approach in which a model is trained using manually annotated data with 
predefined topics. After training, the model accurately classifies unseen texts according to their topics. 
On the other hand, topic modelling is an unsupervised learning approach in which the model identifies the topics by 
detecting the patterns such as words clusters and frequencies. The outputs of a topic model are;
1. clusters of documents that the model has grouped based on topics and 
2. clusters of words (topics) that the model has used to infer the relations.

## How does it work ?

LDA assumes that documents are composed of words that help determine the topics and maps documents to a list of topics 
by assigning each word in the document to different topics. The assignment is in terms of conditional probability 
estimates. We need to compute the probability of a word wj belonging to topic tk. ‘j’ and ‘k’ are the word and topic indices respectively. 
It is important to note that LDA ignores the order of occurrence of words and the syntactic information. 
It treats documents just as a collection of words or a bag of words. 

Once the probabilities are estimated, finding the collection of words that represent a given topic 
can be done either by picking top ‘r’ probabilities of words or by setting a threshold 
for probability and picking only the words whose probabilities are greater than or equal to the threshold value.

Pseudo-code :

        1. Randomly assign each word w in each document to one of the K topics
        2. For each document d:
            a. Asumme that all topic assignments except for the current one are correct
            b. Calculate two proportions
                i)  Proportion of words in document d that are currently assigned to topic t (i.e : p(topic t | document d))
                ii) Proportion of assignments to topic t over all documents that come from this word w (i.e : p(word w | topic t))
            c. Multiply those two proportions and assign to word w a new topic based on that probability. 
        3. Eventually we will reach a steady state where assignments make sense

## Hyperparameters in LDA

LDA has three hyper parameters;
1. document-topic density factor ‘α’
2. topic-word density factor ‘β’
3. the number of topics ‘K’ to be considered. 

alpha=0.1 and beta=0.0002 are generally good starting point.
The lower alpha, the fewer topics per document.
alpha should be low but nonzero so that words can group by document as well.
The lower beta, more extreme each topic's word frequencies

## Data preprocessing for LDA

The typical preprocessing steps before performing LDA are
1. tokenization
2. punctuation and special character removal
3. stop word removal
4. lemmatization

## Credits

* Siraj Raval
* [moreene](https://github.com/morreene)
* [Great Learning](https://www.mygreatlearning.com/blog/understanding-latent-dirichlet-allocation/)

