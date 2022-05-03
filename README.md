# Sentiment-Analysis-with-BERT

Aspect-Based Sentiment Analysis with BERT

## Description

### BERT
BERT uses a brilliant way to tokenize sentences along with their positions, called Positional Embedding. It uses sinusoidal positional encoding to embed the position of the token without changing the weights of the token. It uses sin and cos waves for even and odd indices, thus removing duplicate embedding values. The Hugging face library does this automatically for you. BERT has a rule where all sentences start with [CLS] and end with a [SEP] token.
<br>
BERT also uses a concept called word-piece tokenization which breaks uncommon words into sub words, thus extracting more information from the vocabulary. The Hugging face library’s tokenizer returns IDs, masks and segments. The IDs are the encodings and the masks help in focusing on the non padded parts of the sentences. We do not use segments in our case (DistillBERT), as segments are used to divide sentences into question/answers or other types of sentences. 
<br>
We input the sentences into a BERT Tokenize function along with the DistillBERT Tokenizer. For each type of data (Train, Dev and Test), we tokenize the sentences that return IDs, masks and segments. We store the IDs and masks in separate lists.

### Model 1
We add the aspect and review in the same sentence, separated by a [SEP] token. Therefore we first concatenate the review and the aspect of each sentence into a list. Then we input the sentence into the BERT tokenizer function along with the DistillBERT Tokenizer to get the IDs and masks for each sentence. We store them in lists along with their padding to max length. We make sure the lists are converted to arrays. <br>
The code for the model 1 is run and the results are evaluated. We see an accuracy of 73.8% which is much better than Glove, that just uses traditional words like tokens. The difference between the models is the word embedding used (Glove vs BERT). BERT uses attention as well as positional encoding to understand the contextual relationship of the words, thus resulting in better accuracy. BERT learns its custom word-piece embeddings jointly with the entire model. 

### Model 2
Model 2 uses a Neural Bag of words along with BERT which is able to learn weights of how important each word is. NBOW is able to learn the word importance weights which is a new weighted sum composition of the BERT word vectors. This helps the model achieve an 83.7% accuracy.

### Model 3
We add a CNN layer, with filter size 6, to the NBOW model to get model 3. The CNN uses a window of concatenated words instead of all words in model 2 (NBOW). This assigns equal importance to each word and shows a slightly better performance than model 2. Therefore, we see the evaluated result and the accuracy for this model is  83.9%. 


## Getting Started

### Dependencies

* Python
* Tensorflow
* Keras
* Transformers (huggingface)
* Matplotlib
* Numpy
* Requests

### Installing

* Just download the notebook 

### Executing program

* Run the notebook in a Colab or a jupyter environment


## Help

If you've found a new bug, go ahead and create a new GitHub issue. Be sure to include as much information as possible so I can reproduce the bug.


## Authors

Prof Massimo Poesio
<br>Professor of Computational Linguistics
<br>Queen Mary University of London
