# Word Embeddings

- [Word Embeddings](https://paperswithcode.com/task/word-embeddings) on Papers with Code

## What is word embedding?

In natural language processing (NLP), word embedding is a term used for the representation of words for text analysis, typically in the form of a real-valued vector that encodes the meaning of the word such that the words that are closer in the vector space are expected to be similar in meaning.

In computational linguistics, we often prefer the term **distributional semantic model** (since the underlying semantic theory is called [distributional semantics](https://en.wikipedia.org/wiki/Distributional_semantics)). There are also many other alternative terms in use, from the very general **distributed representation** to the more specific **semantic vector space** or simply **word space**.

## 📜 A Brief History of Word Embeddings

The underlying idea that _"a word is characterized by the company it keeps"_ was proposed in a **1957** article by [**John Rupert Firth**](https://en.wikipedia.org/wiki/J._R._Firth), but also has roots in the contemporaneous work on search systems and in cognitive psychology.

The _first generation of semantic space models_ is the vector space model for information retrieval. Such vector space models for words and their distributional data implemented in their simplest form results in a very sparse vector space of high dimensionality (cf. Curse of dimensionality). Reducing the number of dimensions using linear algebraic methods such as singular value decomposition then led to the introduction of latent semantic analysis in the late 1980s and the Random indexing approach for collecting word cooccurrence contexts. 

Methods for using automatically generated contextual features were developed more or less simultaneously around 1990 in several different research areas. One of the most influential early models was [**Latent Semantic Analysis/Indexing (LSA/LSI)**](https://en.wikipedia.org/wiki/Latent_semantic_analysis), developed in the context of information retrieval, and the precursor of today’s **topic models**.

At roughly the same time, there were several different models developed in research on artificial neural networks that used contextual representations. The most well-known of these are probably [**Self Organizing Maps (SOM)**](https://en.wikipedia.org/wiki/Self-organizing_map) and [**Simple Recurrent Networks (SRN)**](https://en.wikipedia.org/wiki/Recurrent_neural_network), of which the latter is the precursor to today’s neural language models.

Later developments are basically only refinements of these early models. Topic models are refinements of LSA, and include methods like [**probabilistic LSA (PLSA)**](https://en.wikipedia.org/wiki/Probabilistic_latent_semantic_analysis) and [**Latent Dirichlet Allocation (LDA)**](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation). **Neural language models** are based on the same application of neural networks as SRN, and include architectures like [**Convolutional Neural Networks (CNN)**](https://en.wikipedia.org/wiki/Convolutional_neural_network) and [**Autoencoders**](https://en.wikipedia.org/wiki/Autoencoder). **Distributional semantic models** includes models like [**Random Indexing**](https://en.wikipedia.org/wiki/Random_indexing) and [**BEAGLE**](http://www.indiana.edu/~clcl/BEAGLE/).

The main difference between these various models is the type of contextual information they use. LSA and topic models use documents as contexts, which is a legacy from their roots in information retrieval. Neural language models and distributional semantic models instead use words as contexts, which is arguably more natural from a linguistic and cognitive perspective. These different contextual representations capture different types of semantic similarity; the document-based models capture **semantic relatedness** _(e.g. “boat” – “water”)_ while the word-based models capture **semantic similarity** _(e.g. “boat” – “ship”)_. This very basic difference is too often misunderstood.

In 2000 Bengio et al. provided in a series of papers the "Neural probabilistic language models" to reduce the high dimensionality of words representations in contexts by "learning a distributed representation for words".

Most new word embedding techniques after about 2005 rely on a neural network architecture instead of more probabilistic and algebraic models, since some foundational work by _Yoshua Bengio_ and colleagues.

Bengio et al. refer to word embeddings as **distributed representations of words** in 2003 and train them in a neural language model jointly with the model's parameters. First to show the utility of pre-trained word embeddings were arguably Collobert and Weston in 2008. Their landmark paper _"A unified architecture for natural language processing"_ not only establishes word embeddings as a useful tool for downstream tasks, but also introduces a neural network architecture that forms the foundation for many approaches. 

The approach has been adopted by many research groups after advances around year 2010 had been made on theoretical work on the quality of vectors and the training speed of the model and hardware advances allowed for a broader parameter space to be explored profitably. In 2013, a team at Google led by [Tomas Mikolov](https://en.wikipedia.org/wiki/Tomas_Mikolov) created word2vec, a word embedding toolkit that can train vector space models faster than the previous approaches. The [word2vec](https://en.wikipedia.org/wiki/Word2vec) approach has been widely used in experimentation and was instrumental in raising interest for word embeddings as a technology, moving the research strand out of specialised research into broader experimentation and eventually paving the way for practical application.

> However, the eventual popularization of word embeddings can be attributed to Mikolov et al. in 2013 who created word2vec, a toolkit that can train vector space models faster than the previous approaches, allows the seamless training and use of pre-trained embeddings. In 2014, Pennington et al. released GloVe, a competitive set of pre-trained word embeddings.

Historically, one of the main limitations of static word embeddings or word [vector space models](https://en.wikipedia.org/wiki/Vector_space_model) is that words with multiple meanings are conflated into a single representation (a single vector in the semantic space). In other words, [polysemy](https://en.wikipedia.org/wiki/Polysemy) and [homonymy](https://en.wikipedia.org/wiki/Homonym) are not handled properly. For example, in the sentence "The club I tried yesterday was great!", it is not clear if the term club is related to the word sense of a _[club sandwich](https://en.wikipedia.org/wiki/Club_sandwich), [baseball club](https://en.wikipedia.org/wiki/Baseball), [clubhouse](https://en.wikipedia.org/wiki/Meeting_house), [golf club](https://en.wikipedia.org/wiki/Golf_club)_, or any other sense that _club_ might have. The necessity to accommodate multiple meanings per word in different vectors (multi-sense embeddings) is the motivation for several contributions in NLP to split single-sense embeddings into multi-sense ones.

As of the late 2010s, contextually-meaningful embeddings such as [ELMo](https://en.wikipedia.org/wiki/ELMo) and [BERT](https://en.wikipedia.org/wiki/BERT_(language_model)) have been developed. Unlike static word embeddings, these embeddings are at the token-level, in that each occurrence of a word has its own embedding. These embeddings better reflect the multi-sense nature of words, because occurrences of a word in similar contexts are situated in similar regions of BERT’s embedding space.

### 📄 Articles

- [On word embeddings - Part 1](https://ruder.io/word-embeddings-1/index.html) by Sebastian Ruder
- [A Brief History of Word Embeddings | Gavagai](https://www.gavagai.io/text-analytics/a-brief-history-of-word-embeddings/)

## Classification of Word Embeddings

> **Vector space model** or **term vector model** is an algebraic model for representing text documents (and any objects, in general) as vectors of identifiers (such as index terms). It is used in **_information filtering, information retrieval, indexing and relevancy rankings_**. 
> **Semantics:** In linguistics, semantics is the subfield that studies meaning. Semantics can address meaning at the levels of words, phrases, sentences, or larger units of [discourse](https://en.wikipedia.org/wiki/Discourse). 

### Count based Vector Space Model (Non-semantic)

- Bag-of-words model
- TF-IDF (Term Frequency, Inverse Document Frequency)
- Hashing Vectorization

### Non Context-Based Vector Space Model (Semantic)

- Word2Vec
  - Continuous Bag-of-Words Model
  - Continuous Skip-gram Model
- FastText
- GloVe

### Context-Based Vector Space Model (Semantic)

- ELMo
- Transformers (BERT)

### Other

- Ohe-hot encoding

## 

- [TF-IDF Vectorizer](https://github.com/ElizaLo/NLP-Natural-Language-Processing/tree/master/Word%20Embedings/TF-IDF%20Vectorizer)

  1. ### **_Word Embedings_**
      - **One-hot encoding**
      - **Feature vectors**
      - **Cooccurrence vectors**
      - **Sparse Distributed Representations (SDRs)**
      ----------------
      - **Static Word Embeddings:**
        - **Continuous Bag-of-Words (CBOW)**
          - [Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/pdf/1301.3781.pdf)
        - **Skip-gram Model**
          - [Distributed Representations of Words and Phrases and their Compositionality](https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf)
          - [Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/pdf/1301.3781.pdf)
        - **Word2Vec**
          - Continuous Bag-of-Words Model
          - Continuous Skip-gram Model
        - **FastText**
          - [Bag of Tricks for Efficient Text Classification](https://arxiv.org/pdf/1607.01759.pdf)
          - [Enriching Word Vectors with Subword Information](https://arxiv.org/pdf/1607.04606.pdf)
          - [FASTTEXT.ZIP:COMPRESSING TEXT CLASSIFICATION MODELS](https://arxiv.org/pdf/1612.03651.pdf)
        - **GloVe: Global Vectors for Word Representation**
          - [GloVe: Global Vectors for Word Representation Article](https://nlp.stanford.edu/pubs/glove.pdf)
          - [GloVe](https://nlp.stanford.edu/projects/glove/)
       -------------------------
      - **Deep Neural Networks for Word Representations:** 
        - **Sequence to Sequence Model (Seq2Seq)**
          - [Sequence to Sequence Learning with Neural Networks](https://arxiv.org/pdf/1409.3215.pdf)
          - [Order Matters: Sequence to sequence for sets](https://arxiv.org/pdf/1511.06391.pdf)
          - [A Comparison of Sequence-to-Sequence Models for Speech Recognition](https://www.isca-speech.org/archive/Interspeech_2017/pdfs/0233.PDF)
          - [Sequence to Sequence – Video to Text](https://www.cs.utexas.edu/users/ml/papers/venugopalan.iccv15.pdf)
          - [Understanding Encoder-Decoder Sequence to Sequence Model](https://towardsdatascience.com/understanding-encoder-decoder-sequence-to-sequence-model-679e04af4346)
      ----------------------------
      - **Contextualized (Dynamic) Word Embeddings (LM):**
         - CoVe (Contextualized Word-Embeddings)
         - CVT (Cross-View Training)
         - ELMO (Embeddings from Language Models)
            - [Deep contextualized word representations](https://arxiv.org/pdf/1802.05365.pdf)
         - ULMFiT (Universal Language Model Fine-tuning)
         - BERT (Bidirectional Encoder Representations from Transformers)
            - [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/pdf/1810.04805.pdf)
            - [FROM Pre-trained Word Embeddings TO Pre-trained Language Models — Focus on BERT](https://medium.com/@adriensieg/from-pre-trained-word-embeddings-to-pre-trained-language-models-focus-on-bert-343815627598)
         - GPT & GPT-2 (Generative Pre-Training)
         - Transformer XL (meaning extra long)
         - XLNet (Generalized Autoregressive Pre-training)
         - ENRIE (Enhanced Representation through kNowledge IntEgration)
         - (FlairEmbeddings (Contextual String Embeddings for Sequence Labelling))
---------------------------
  2. ### **_Sentence Embedings_**
      - [How to obtain Sentence Vectors?](https://medium.com/explorations-in-language-and-learning/how-to-obtain-sentence-vectors-2a6d88bd3c8b)
      - [Deep-learning-free Text and Sentence Embedding](https://www.offconvex.org/2018/06/17/textembeddings/)
-------------------------------------------------------      
  3. ### **_Text / Document Embedings_**
      - [Document Embedding Techniques](https://towardsdatascience.com/document-embedding-techniques-fed3e7a6a25d)

-----------------------------------------------------------------------

# Count based Vector Space Model (Non-semantic)

## One-hot encodding

> Also known as _**“1-of-N”**_ encoding (meaning the vector is composed of a single one and a number of zeros).

In one hot encoding, every word (even symbols) which are part of the given text data are written in the form of vectors, constituting only of **1** and **0**. So one hot vector is a vector whose elements are only 1 and 0. 

**Each word is written or encoded as one hot vector, with each one hot vector being unique.** This allows the word to be identified uniquely by its one hot vector and vice versa, that is no two words will have same one hot vector representation.

### Pros and Cons

➕ **Pros:**

- One-hot encoding ensures that machine learning does not assume that higher numbers are more important. For example, the value '8' is bigger than the value '1', but that does not make '8' more important than '1'. The same is true for words: the value 'laughter' is not more important than 'laugh'.
- One-Hot-Encoding has the advantage that the result is binary rather than ordinal and that everything sits in an orthogonal vector space.

➖ **Cons:**

- Curse of **dimensionality**, which refers to all sorts of problems that arise with data in high dimensions. Even with relatively small eight dimensions, our example text requires exponentially large memory space. Most of the matrix is taken up by zeros, so useful data becomes sparse. Imagine we have a vocabulary of 50,000. (There are roughly a million words in English language.) Each word is represented with 49,999 zeros and a single one, and we need 50,000 squared = 2.5 billion units of memory space. Not computationally efficient.
- **Hard to extract meanings.** Each word is embedded in isolation, and every word contains a single one and N zeros where N is the number of dimensions. The resulting set of vectors do not say much about one another. If our vocabulary had _“orange”, “banana”_ and _“watermelon”_, we can see the similarity between those words, such as the fact that they are types of fruit, or that they usually follow some form of the verb _“eat”_. We can easily form a mental map or cluster where these words exist close to each other. But with one-hot vectors, all words are equal distance apart.
- Another disadvantage of one-hot encoding is that it produces **multicollinearity** among the various variables, lowering the model's accuracy.

### 📰 Articles

- [One-hot](https://en.wikipedia.org/wiki/One-hot)
- [One Hot encoding of text data in Natural Language Processing](https://medium.com/analytics-vidhya/one-hot-encoding-of-text-data-in-natural-language-processing-2242fefb2148)
- [How to One Hot Encode Sequence Data in Python](https://machinelearningmastery.com/how-to-one-hot-encode-sequence-data-in-python/)
- [One Hot Encoding to treat Categorical data parameters](https://www.geeksforgeeks.org/ml-one-hot-encoding-of-datasets-in-python/)
- [Natural Language Processing: Count Vectorization with scikit-learn](https://towardsdatascience.com/natural-language-processing-count-vectorization-with-scikit-learn-e7804269bb5e)

### Implementation

- [sklearn.preprocessing.OneHotEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)
- [Keras: to_categorical-function]([https://keras.io/api/utils/#to_categorical](https://keras.io/api/utils/python_utils/#to_categorical-function))

## Bag-of-words model (BoW)

In this model, a text (such as a sentence or a document) is represented as the [bag (multiset)](https://en.wikipedia.org/wiki/Multiset) of its words, disregarding grammar and even word order but keeping multiplicity.

> **Count vectorizer** creates a matrix with documents and token counts (bag of terms/tokens) therefore it is also known as **document term matrix**.

CountVectorizer tokenizes(tokenization means dividing the sentences in words) the text along with performing very basic preprocessing. It removes the punctuation marks and converts all the words to lowercase.
The vocabulary of known words is formed which is also used for encoding unseen text later.
An encoded vector is returned with a length of the entire vocabulary and an integer count for the number of times each word appeared in the document. The image below shows what I mean by the encoded vector.

The row of the above matrix represents the document, and the columns contain all the unique words with their frequency. In case a word did not occur, then it is assigned zero correspondings to the document in a row.
Imagine it as a one-hot encoded vector and due to that, it is pretty obvious to get a sparse matrix with a lot of zeros.

### Pros and Cons

➕ **Pros:**

- The most significant advantage of the bag-of-words model is its simplicity and ease of use.

➖ **Cons:**

- The vocabulary/dictionary needs to be designed very carefully. Considering its size has an impact on the sparsity of the document representations and must be managed well.
- The model **ignores context** by discarding the meaning of the words and focusing on the frequency of occurrence. This can be a major problem because the arrangement of the words in a sentence can completely change the meaning of the sentence and the model cannot account for this.
- Another major drawback of this model is that it is rather **difficult to model [sparse representations](https://en.wikipedia.org/wiki/Sparse_approximation)**. This is due to informational reasons as well as computational reasons. The model finds it difficult to harness a small amount of information in a vast representational space.
- If the new sentences contain new words, then our vocabulary size would increase and thereby, the length of the vectors would increase too. Additionally, the vectors would also contain many 0s, thereby resulting in a sparse matrix (which is what we would like to avoid).

### 📰 Articles

- [Bag of words model](https://thatascience.com/learn-machine-learning/bag-of-words/)
- [10+ Examples for Using CountVectorizer](https://kavita-ganesan.com/how-to-use-countvectorizer/#.YGMSUy1c5WO)
- [Bag of words Model](https://www.engati.com/glossary/bag-of-words)
- [All You Need to Know About Bag of Words and Word2Vec — Text Feature Extraction](https://towardsdatascience.com/all-you-need-to-know-about-bag-of-words-and-word2vec-text-feature-extraction-e386d9ed84aa)

### Implmentation 

- [Counting words in Python with sklearn's CountVectorizer](https://investigate.ai/text-analysis/counting-words-with-scikit-learns-countvectorizer/)
- [Basics of CountVectorizer](https://towardsdatascience.com/basics-of-countvectorizer-e26677900f9c)

## N-gram Language Models

> An n-gram model is a type of probabilistic [language model](https://en.wikipedia.org/wiki/Language_model) for predicting the next item in such a sequence in the form of a (n − 1)–order [Markov model](https://en.wikipedia.org/wiki/Markov_chain).

An N-Gram is a connected string of N-items from a sample of text or speech. The N-Gram could be comprised of large blocks of words, or smaller sets of syllables. N-Grams are used as the basis for functioning N-Gram models, which are instrumental in natural language processing as a way of predicting upcoming text or speech.

An n-gram model models sequences, notably natural languages, using the statistical properties of n-grams.

This idea can be traced to an experiment by Claude Shannon's work in information theory. Shannon posed the question: given a sequence of letters (for example, the sequence "for ex"), what is the likelihood of the next letter? From training data, one can derive a probability distribution for the next letter given a history of size _n_: _a = 0.4, b = 0.00001, c = 0, ...._; where the probabilities of all possible "next-letters" sum to 1.0.

More concisely, an n-gram model predicts the next word based on the sequence of previous words.

When used for language modelling, independence assumptions are made so that each word depends only on the last n − 1 word. This Markov model is used as an approximation of the true underlying language. This assumption is important because it massively simplifies the problem of estimating the language model from data. In addition, because of the open nature of language, it is common to group words unknown to the language model together.

Note that in a simple n-gram language model, the probability of a word, conditioned on some number of previous words (one word in a bigram model, two words in a trigram model, etc.) can be described as following a categorical distribution (often imprecisely called a "multinomial distribution").

### Pros and Cons

➕ **Pros:**

- 

➖ **Cons:**

- The major drawback of feature spaces represented by n-gram models is extreme **sparcity**. But even more unsettling is that it can only interpret unseen instances with respect to learned training data. That is, if a classifier learned from the instances _'today was a good day'_ and _'that is a ridiculous thing to say'_, it is unable to say much about the instance _'i love this song!'_ since the features are _'today', 'was', 'a', 'good', 'day', 'that', 'is', 'ridiculous', 'thing', 'to', 'say'_.

### 📚 Books

- [N-gram Language Models](https://web.stanford.edu/~jurafsky/slp3/3.pdf) chapter, _“Speech and Language Processing”_ by Daniel Jurafsky & James H. Martin, 2021.
  - [Nlp - 2.1 - Introduction to N-grams](https://www.youtube.com/watch?v=dkUtavsPqNA)

### 📰 Articles

- [N-Grams](https://deepai.org/machine-learning-glossary-and-terms/n-gram)
- [n-gram](https://en.wikipedia.org/wiki/N-gram), wikipedia

### Implementation

- [N-gram Language Model with NLTK](https://www.kaggle.com/code/alvations/n-gram-language-model-with-nltk), Kaggle notebook

## Co-Occurence Counts/Vectors

Words that are related will often appear in the same documents. For instance, _"banks", "bonds", "stocks", "money"_, etc. are probably likely to appear together. But _"banks", "octopus", "banana"_, and _"hockey"_ would probably not consistently appear together. 

## TF–IDF (Term Frequency, Inverse Document Frequency)

TF-IDF (Term Frequency, Inverse Document Frequency) is a numerical statistic that is intended to reflect how important a word is to a document in a collection or [corpus](https://en.wikipedia.org/wiki/Text_corpus). The tf–idf value increases proportionally to the number of times a word appears in the document and is offset by the number of documents in the corpus that contain the word, which helps to adjust for the fact that some words appear more frequently in general.

**This is done by multiplying two metrics:** how many times a word appears in a document, and the inverse document frequency of the word across a set of documents.

- **Term Frequency** of a word in a document. There are several ways of calculating this frequency, with the simplest being a raw count of instances a word appears in a document. Then, there are ways to adjust the frequency, by the length of a document, or by the raw frequency of the most frequent word in a document.
- **Inverse Document Frequency** of the word across a set of documents. This means, how common or rare a word is in the entire document set. The closer it is to 0, the more common a word is. This metric can be calculated by taking the total number of documents, dividing it by the number of documents that contain a word, and calculating the logarithm.

So, if the word is very common and appears in many documents, this number will approach 0. Otherwise, it will approach 1.

Multiplying these two numbers results in the TF-IDF score of a word in a document. The higher the score, the more relevant that word is in that particular document.

A survey conducted in 2015 showed that 83% of text-based recommender systems in digital libraries use TF–IDF.

TF-IDF was invented for document search and information retrieval. It works by increasing proportionally to the number of times a word appears in a document but is offset by the number of documents that contain the word. So, words that are common in every document, such as _the_, _a_, and _of_, rank low even though they may appear many times since they don’t mean much to that document in particular.

However, if the word _Politics_ appears many times in a document, while not appearing many times in others, it probably means that it’s very relevant.

### Pros and Cons

➕ **Pros:**

- The biggest advantages of TF-IDF come from how **simple and easy to use it** is. It is simple to calculate, it is computationally cheap, and it is a simple starting point for similarity calculations (via TF-IDF vectorization + cosine similarity).
- You have some basic metric to extract the most descriptive terms in a document.
- You can easily compute the similarity between 2 documents using it.

➖ **Cons:**

- The drawback of this method is that it **doesn’t hold the semantic meaning of the words**.
- TF-IDF is based on the bag-of-words (BoW) model, therefore it does not capture position in text, co-occurrences in different documents, etc. For this reason, TF-IDF is only useful as a lexical level feature.

### 📚 Books

- [6. Vector Semantics and Embeddings](https://web.stanford.edu/~jurafsky/slp3/6.pdf), 6.5 TF-IDF: Weighing terms in the vector, page 11, "Speech and Language Processing" by Daniel Jurafsky & James H. Martin.
  - [Vector 5 TF IDF](https://www.youtube.com/watch?v=TBUpxFw8oIA&list=PLaZQkZp6WhWxIvz74aEvvVc99o7WuOoQ6&index=6)
  - [TF-IDF](https://web.stanford.edu/~jurafsky/slp3/slides/6_Vector_Apr18_2021.pdf), slides

### 📰 Articles

- [TF–IDF](https://en.wikipedia.org/wiki/Tf–idf), Wikipedia
- [The Ultimate Guide To Different Word Embedding Techniques In NLP - KDnuggets](https://www.kdnuggets.com/2021/11/guide-word-embedding-techniques-nlp.html)

### Implementation

- [sklearn.feature_extraction.text.TfidfVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html)
- [TF-IDF with Scikit-Learn](https://melaniewalsh.github.io/Intro-Cultural-Analytics/05-Text-Analysis/03-TF-IDF-Scikit-Learn.html)
- [Text Vectorization Using Python: TF-IDF](https://okan.cloud/posts/2022-01-16-text-vectorization-using-python-tf-idf/)
- [TF IDF | TFIDF Python Example](https://towardsdatascience.com/natural-language-processing-feature-engineering-using-tf-idf-e8b9d00e7e76)

------

# Non-Context-Based Vector Space Model (Semantic)

## Word2Vec

- 📄 **Paper:** [Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/abs/1301.3781), 16 Jan 2013 by Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean

Word2Vec was presented in two initial papers released within a month of each other. The original authors are a team of researchers from Google.

### Continuous Bag-of-Words Model

- [Papers with Code - CBoW Word2Vec Explained](https://paperswithcode.com/method/cbow-word2vec)

### Continuous Skip-gram Model

- [Papers with Code - Skip-gram Word2Vec Explained](https://paperswithcode.com/method/skip-gram-word2vec)

### 📄 Papers

- **Original Paper:** [Efficient Estimation of Word Representations in Vector Space](https://arxiv.org/abs/1301.3781), 16 Jan 2013 by Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean
  - [Papers with Code - Efficient Estimation of Word Representations in Vector Space](https://paperswithcode.com/paper/efficient-estimation-of-word-representations)
  - [Papers with Code - word2vec Explained: deriving Mikolov et al.'s negative-sampling word-embedding method](https://paperswithcode.com/paper/word2vec-explained-deriving-mikolov-et-als)
- [Exploiting Similarities among Languages for Machine Translation](https://arxiv.org/abs/1309.4168), 17 Sep 2013 by Tomas Mikolov, Quoc V. Le, Ilya Sutskever
- [Distributed Representations of Words and Phrases and their Compositionality](https://arxiv.org/abs/1310.4546), 16 Oct 2013 by Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg Corrado, Jeffrey Dean
- [Papers with Code - CBoW Word2Vec Explained](https://paperswithcode.com/method/cbow-word2vec)
- [Papers with Code - Skip-gram Word2Vec Explained](https://paperswithcode.com/method/skip-gram-word2vec)

### 📰 Articles

- [Word2Vec Resources · Chris McCormick](http://mccormickml.com/2016/04/27/word2vec-resources/#original-papers--resources-from-google-team)
- [Word2Vec Tutorial](http://mccormickml.com/2017/01/11/word2vec-tutorial-part-2-negative-sampling/)
- 
- [Implementing Deep Learning Methods and Feature Engineering for Text Data: The Continuous Bag of Words (CBOW)](https://www.kdnuggets.com/2018/04/implementing-deep-learning-methods-feature-engineering-text-data-cbow.html)

------

## Tokenization

### Readady Solutions

| Title | Description, Information |
| :---:         |          :--- |
|[Tokenizers](https://github.com/huggingface/tokenizers)|Fast State-of-the-Art Tokenizers optimized for Research and Production by [HuggingFace](https://huggingface.co/)|

------

## 📚 Books

- [6. Vector Semantics and Embeddings](https://web.stanford.edu/~jurafsky/slp3/6.pdf), “Speech and Language Processing” by Daniel Jurafsky & James H. Martin

------

## Courses, Videos

- [Week 4: Vector Semantics and Embeddings](https://www.youtube.com/playlist?list=PLaZQkZp6WhWxIvz74aEvvVc99o7WuOoQ6), by Dan Jurafsky

------

## 📰 Articles

- [Word embedding](https://en.wikipedia.org/wiki/Word_embedding), Wikipedia
- [A Brief History of Word Embeddings | Gavagai](https://www.gavagai.io/text-analytics/a-brief-history-of-word-embeddings/)
- [On word embeddings - Part 1](https://ruder.io/word-embeddings-1/index.html), 
- [A Complete Guide To Understand Evolution of Word to Vector](https://medium.com/co-learning-lounge/nlp-word-embedding-tfidf-bert-word2vec-d7f04340af7f)
- [Word Embedding in NLP: One-Hot Encoding and Skip-Gram Neural Network](https://towardsdatascience.com/word-embedding-in-nlp-one-hot-encoding-and-skip-gram-neural-network-81b424da58f2)
- [Everything about Embeddings](https://medium.com/@b.terryjack/nlp-everything-about-word-embeddings-9ea21f51ccfe)
- [The Ultimate Guide To Different Word Embedding Techniques In NLP - KDnuggets](https://www.kdnuggets.com/2021/11/guide-word-embedding-techniques-nlp.html)

---
- [Language model](https://en.wikipedia.org/wiki/Language_model)

------

## Implementation

- [Word embeddings  |  Text  |  TensorFlow](https://www.tensorflow.org/text/guide/word_embeddings)

-------

## Models

### Sentence Embedings

| Title | Description, Information |
| :---:         |          :--- |
|[SentEval: evaluation toolkit for sentence embeddings](https://github.com/facebookresearch/SentEval)|SentEval is a library for evaluating the quality of sentence embeddings. We assess their generalization power by using them as features on a broad and diverse set of "transfer" tasks. SentEval currently includes 17 downstream tasks. We also include a suite of 10 probing tasks which evaluate what linguistic properties are encoded in sentence embeddings. Our goal is to ease the study and the development of general-purpose fixed-size sentence representations.|
|[HMTL (Hierarchical Multi-Task Learning model)](https://github.com/huggingface/hmtl)|HMTL is a Hierarchical Multi-Task Learning model which combines a set of four carefully selected semantic tasks (namely Named Entity Recoginition, Entity Mention Detection, Relation Extraction and Coreference Resolution). The model achieves state-of-the-art results on Named Entity Recognition, Entity Mention Detection and Relation Extraction. Using [SentEval](https://github.com/facebookresearch/SentEval), we show that as we move from the bottom to the top layers of the model, the model tend to learn more complex semantic representation.|
