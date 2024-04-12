CS366-Project: Neural Machine Translation
Author: Munesh Meena 
Roll NO. 2101cs47
1.Description of Files:-
 data-processing.ipynb:
provided files.
Cleaning, sampling, analysis and addition of starting and end tokens to the
 embedding.ipynb: Using fasttext and word2vec for hindi and english embeddings respectively and
storing the resulting mapping in a pickle object.
 model.ipynb: Tensorflow and keras used to create a NMT model using vanilla RNNs. The predictions
are also carried out in this notebook.
 metrics.ipynb: Bleu score and relevant statistics calculated.
 raw train.csv: Training files read and stored in a csv.
 raw test.csv: Test files read and stored in a csv.
 train.csv: Cleaned train files.
 test.csv: Cleaned test files.
 hindi model.ipynb: Stores fasttext embeddings of hindi words.
 hindi model.ipynb: Stores word2vec embeddings of english words.
 preds.csv: Stores the predicted and actual hindi sentences, used for calculating metrics.
2.Data Analysis and Processing:-The data was cleaned by removing punctuations, special symbols and numbers. Even after doing so, it was
observed that there were few latin characters and words present in hindi words. 30% of training and testing
data was also chosen at this stage.
It was also evident that the number of words in a sentence ranged from as low as 1 to as high as 117 however,
majority of words ¿75% were smaller than 20. So, a design choice was made to exclude sentences above 20
words for both training and testing data. This also helped to simplify the model complexity.
The total english words stood at 4123 lower than hindi words at 5042. Also while calculating the embeddings,
it was found that 1382 and 1385 of the english and hindi words embedding were not found.
3.Methodology and Model:-A sentence was encoded by first adding ¡sos¿ and ¡eos¿ tokens and then mapping the words to their embeddings.
The encoder of the model takes these embedding as inputs and passes them through a linear layer that maps
it to a 450 dimensional vector, this is then passed through a rnn to get the hidden state representation.
The decoder further takes the hidden state passes it through a rnn embedding of matching dimension, the
output representation is passed to a dense layer with softmax as activation to obtain the required output.
4.Training the Model:-For training the models the decoder was fed the final state from the encoder layer and for input it was given
the real token from the actual data. The model was trained for 135 epochs on CPU using RMSprop and log
loss as optimizer and loss function respectively.
5.Testing the Model:-Here the previously predicted output of the model was fed as input instead of the actual data (as was done for
training). The english sentence, the targetted hindi sentences were saved in a file by the name of preds.csv.
6.Result:-The relevant statistic regarding BLEU scores are encapsulated in table 1-
Bleu statistic

Conclusion
Given the results, we can say that the model performs satisfactory given the simplicity of our approach. If
the data quality were to be improved and most importantly the embeddings were created on the dataset, this
simple model would have fated better.
