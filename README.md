# Language-Modelling---Movie-Reviews
Generate movie reviews for torchtext IMDB dataset using LSTM based Language Model

## 1) Built a Markov (n-gram) language model

Have a markov model trigram model. Torch test was used to retrieve the IMDB dataset and custom function generate trigrams is passed to the preprocessing argument in the data.
Used field function to put each review into trigrams and freqs function is used to get the count of each trigram.
This data is further manipulated to calculate probabilties and predictions are made my smapling these probabilities.

## 1) Built an LSTM based language model

Used the trigrams and there was no difficulty in calculating the probabilities and prediction.

For LSTM there was an input layer followed by embedding then lstm layer. 
The input was the tokenized text and output also the tokenized text offsetted by 1 place. 
Ex) if input is [This,is,my,favorite,movie] then output is [is,my,favorite,movie,<>]. If you give the word "This" then model should predict "is" and so on. Due to the size of the input training model with a decent training size became a struggle.

## Issues faced

Took 25% training data with max 1000 words with batch size 10 to train the LSTM model.
If we increased the number of words then the model couldn't be loaded into the GPU as there was insufficient memory
If we increased the training data to higher percentage say 50% or 80% then notebook got disconnected from the server randomly. 
This error didn't go when I tried to run the code as standalone .py file instead of a python notebook.
When I reduced the batch size to 1 then model took longer time to train and when we increased it to 64 then there was memory error once again. We settled at Batch Size 10
Due to this limited training size and words the quality of sentence formed by predicition was affected considerably.
The prediction didn't give out a coherent sentence as we would have liked.

### Generated predictions for both Markov (n-gram) language model and LSTM based language model.
