# Alice in wonderland text generation
Generate text based on the codependencies between characters
Use the previous 100 characters to predict the next character.
Credit: Deep Learning with Python by Jason Brownlee
data source: http://www.gutenberg.org/cache/epub/11/pg11.txt

## Preprocess
1. convert all text to lower case
2. convert characters to integers
<img src = "https://github.com/sindhri/Alice/blob/master/doc/img1.png" width = "800">
3. set up sequences of consecutive 100 characters for training
4. reshape
5. normalize
6. encode the character to be predicted

## 1. Alice_small: a small LSTM
<img src = "https://github.com/sindhri/Alice/blob/master/doc/img2.png" width = "500">
A single hidden LSTM layer with 256 memory units.  
A dropout layer with a probability of 20%.  
A Denselayer with softmax.   
Took almost 12 hours to complete.

## 2. Alice_large: a large LSTM
<img src = "https://github.com/sindhri/Alice/blob/master/doc/img3.png" width = "500">
Probably will take 2 days to complete!

## 3. Use Alice_small to generate 1000 characters
The 20th iteration has the best result so used the weights from there.

Seed:
" ('i haven't,' said
alice)--'and perhaps you were never even introduced to a lobster--'
(alice began  "

Output:
"to tand tha lirtle crorer, and the whrt hnsd the rooe of the sore, and the whrt hns loet the rooe  she was toene a little brotee of the tore, ''tha kors  is a goea harder, a dottorn of the soens oi the soed. 

'that so so to tee it a lan,' said the date piitled an in aaden, and she whst hnc ayou dad boen to meke the roeer of the sord, 
'the drese'  she manch hare said to the jury, and the whnt hncd ano the whnt hn with a credt hurre  and eoln tith the dourd oo the tordd aelir it, ''tha lort  if ioursee to that i san it the soies ' 
'the drester the sab ot taad '  io a goer haid oo the grehe of the sore!

 she drchess saveer wo tey in a lont of the soine 
  the hoeh tuiue ard toee tf the soees of the soens oo she shane 'a
dotiouse oo too the white  and the thete ras a lott of thi grere of the caree and aeler whsh an the could. 
'the drehess!s metee tai ' the gatter wand tn alice, 'she was a little brallen on the thnl of the garde hfr hand, and the whrt hns loet the ras and the courd no 
Done."
Pretty nonsense but interesting.

## 4. Use Alice_large to generate 1000 characters
Only had time to run 14 iterations.  
Seed:
" herself very good advice, (though she very seldom followed it),
and sometimes she scolded herself so "  

Output:
"herself in a little boot and she had gooe of the soof, and she had not a little gooden sure the court, and she semembered the court, and she serser the had not a little gooden sure, and she shought it was a little boot and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she had not a little boot and she had not a little boot and she had not and she had not a little boot and she 
Done."  

Since it was only trained slightly, it has a lot of repetitions. 

# Conclusion: small network that was able to complete more iteration performs better!

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
