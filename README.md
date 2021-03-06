# END2_Assignment6
### a note on file names
*Model A*: **61_RNN** This notebook contains the implementation of  Model A.  <br/>

*Model B*: **62_LSTMCell** This notebook contains the implementation of Model B.<br/>

## Background
In this assignment we were asked to build an encoder/decoder model for Tweets dataset, where 
the encoder: an RNN/LSTM layer takes the words in a sentence one by one and finally converts them into a single vector.
This single vector is then sent to another RNN/LSTM that also takes the last prediction as its second input.
Then we take the final vector and send to a Linear Layer and make the final prediction.
Once the model is trained, take one sentence, print the outputs of the encoder for each step and
print the outputs for each step of the decoder. 
## Approach
### Architecture
Two different appraoches for this encoder/decoder Model were implemented (Model A and Model B) as depicted below:
#### Model A 
![image](https://user-images.githubusercontent.com/82941475/121353803-e2384200-c94b-11eb-8141-6d84eaa1a0d1.png)
#### Model B
![image](https://user-images.githubusercontent.com/82941475/121353924-0005a700-c94c-11eb-96cc-9a0b9f6a37c8.png)
### Salient Features 
#### Model A: 
- Both encoder and decoder are implemented using RNN, single layer.
- Last single vector (the last hidden output) is passed to decoder's hidden input. 
- The input to the decoder is output of encoder which is the stacked hidden states of encoder.
- Validation Accuracy: 73.21%

#### Model B:
- Encoder is implemented as RNN, decoder is implemented as LSTMCell, which is looped over the length of the sentence.
- Last single vector (the last hidden output) is passed to decoder's hidden input. 
- The input to the first step of decoder is the last hidden  output of encoder 
- The input to next time steps are the hidden state of previous step. 
- Since this is the LSTMCell, a cell state initialized to zero is also passed to the decoder.
- Validation Accuracy: 68.30% 

### Final Output
The output of both the models is presented as<br/>
Tweet: 'If', 'you', 'can', 'find', 'a', 'better', 'Obama', 'gif', 'than', 'this', 'one', ',', 'I', "'m", 'quitting', 'Twitter', '.', 'http://t.co/cNr0Sr3c'
|Word|Encoded|Decoded|
|----|--------|------|
|If  |tensor([-0.1219,  0.6393,  0.8072,  0.0501, .....]) | tensor([-0.5437,  0.0383, -0.3279,  0.2949,......])|
|you |tensor([-1.0572e-01, -3.7647e-01,  3.2657e-01, -3.5636e-01,...])|tensor([-0.4573,  0.2999, -0.4054,  0.4770, -0.6636,....])|
|... |....|...|

#### Results and  discussions
- A typicalilty which was observed with model B was that both training and validation accuracy would soon reach to some value (Most of the times 69.21% and 68.30% respectively ) and would not change after that inspite of increasing the epochs. Though sometimes during the training phase, it was observed that after 50 or so epochs, it will change slightly only to settle back there. It was suspected that either it was stuck in some local minima and was not able to move from there or the overall design is bad that its not helping to improve the accuracy Learnings
- A very painful learning was that squeeze function squeezes out all dimensions which are one. So while trying to predict for single sentence, the hidden vector formed was of 1,1,100 dimensions, which on squeeze became 100 and the error was painful to identify. :((. So always specify the dimension to squeeze rather than just using it unscrupulously.
- Both the models are not doing anthing useful without the attention mechanism in place. Actually after this implementation, it was easy to understand the need, relevance (and possibly implementation) attention mechanism. Thanks for giving this work to make us realize the futility of it (in some ways).

### Group Members
Ritambhra Korpal<br/>
Chaitanya Vanapamala <br/>
Pralay Ramteke <br/>
Pallavi <br/>

