# Alice in wonderland text generation
Generate text based on the codependencies between characters
Use the previous 100 characters to predict the next character.
Credit: Deep Learning with Python by Jason Brownlee
data source: http://www.gutenberg.org/cache/epub/11/pg11.txt

## Preprocess
1. convert all text to lower case
2. convert characters to integers
<img src = "https://github.com/sindhri/Alice/blob/master/doc/img1.png" width = "300">
3. set up sequences of consecutive 100 characters for training
4. reshape
5. normalize
6. encode the character to be predicted

## 1. Alice_small: a small LSTM
<img src = "https://github.com/sindhri/Alice/blob/master/doc/img2.png" width = "500">
A single hidden LSTM layer with 256 memory units.  
A dropout layer with a probability of 20%.  
A Denselayer with softmax.   
Paintfully slow already, probably will take hours to complete


## 2. Alice_large: a large LSTM
<img src = "https://github.com/sindhri/Alice/blob/master/doc/img3.png" width = "500">

take maybe whole night?

## 3. Use Alice_small to generate 1000 characters

## 4. Use Alice_large to generate 1000 characters

# Conclusion: fun but takes forever to train!

# Ways to improve:
* Predict less than 1000 words
* Remove all punctuations except space
* Try one hot encoder for input characters
* Train the model on padded senteces instead of an arbitary of 100 characters
* Increase the training size from 100 to multiple hundreds
* Add drop out and tune percentage
* Tune batch size, size=1 is very slow to size=100
* Add memory units
* Experiment with scale factors (?)
* Change LSTM to stateful
