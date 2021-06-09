# END2_Assignment6
### a note on file names
*Model A*: ** 61_RNN** This notebook contains the following architecture of Model A.  <br/>

*Model B*: **62_LSTMCell** This notebook contains the following architecture of the model B.<br/>

## Background
In this assignment we were asked to build an encoder/decoder model for Tweets dataset, where <br/>
the encoder: an RNN/LSTM layer takes the words in a sentence one by one and finally converts them into a single vector.<br/>
This single vector is then sent to another RNN/LSTM that also takes the last prediction as its second input. <br/>
Then we take the final vector from this Cell and send this final vector to a Linear Layer and make the final prediction.<br/>
Once the model is trained, take one sentence, print the outputs of the encoder for each step and<br/>
print the outputs for each step of the decoder. 
## Approach
### Architecture
Two different appraoches for this encoder/decoder Model were implemented (Model A and Model B) as depicted below:
#### Model A 
![image](https://user-images.githubusercontent.com/82941475/121353803-e2384200-c94b-11eb-8141-6d84eaa1a0d1.png)
#### Model B

### Salient Features (Not Visible in the image)
#### Model A: 
Validation Accuracy:

#### Model B:
Validation Accuracy:
A typicalilty which was happening with this model was that both training and validation accuracy would soon reach 
69.21% and 68.30% respectively and would not change after that inspite of increasing the epochs. Though sometimes during the training phase, it was observed that after 50 or so epochs, it will change slightly only to settle back there.
I was suspecting it was stuck in some local minima and was not able to move from there.

### Final Output
The output of both the models is presented as
Tweet: ['If', 'you', 'can', 'find', 'a', 'better', 'Obama', 'gif', 'than', 'this', 'one', ',', 'I', "'m", 'quitting', 'Twitter', '.', 'http://t.co/cNr0Sr3c']
Word|Encoded|Decoded|
---------------------
If  |tensor([-0.1219,  0.6393,  0.8072,  0.0501, .....])|tensor([-0.5437,  0.0383, -0.3279,  0.2949,......])
you |tensor([-1.0572e-01, -3.7647e-01,  3.2657e-01, -3.5636e-01,...])|tensor([-0.4573,  0.2999, -0.4054,  0.4770, -0.6636,....])
... |....|...
-----------------------

### Group Members
Ritambhra Korpal<br/>
Chaitanya Vanapamala <br/>
Pralay Ramteke <br/>
Pallavi <br/>

