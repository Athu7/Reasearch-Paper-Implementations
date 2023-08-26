# Attention is all you need

# Self attention model

This is an attention mechanism to capture the interrelationship of the tokens in the same sequence. This is a breakthrough attention mechanism as this can perform simulataneously on all the tokens as opposed to the sequential neural networks (RNNs, LSTMs, GRUs). 

The input to the self attention model will be the embeddings of individual tokens in a sequence

![Untitled](Attention%20is%20all%20you%20need%20a3c80a6b34f84e4395186ef8e892402d/Untitled.png)

In this model we have three things (***Queries , Keys , Values***)  we calculate to capture the inter-relationship among the tokens and there are three parameters(***Query matrix, Key matrix, Value matrix***) that are learned to calculate these things.

Every embedding vector is multiplied by the respective matrices to get the repective results. 

![Untitled](Attention%20is%20all%20you%20need%20a3c80a6b34f84e4395186ef8e892402d/Untitled%201.png)

**Number of input tokens: $n$**

**Input embedding dimension: $m$** 

**Hidden dimension: $d_k$**

**Input matrix $X \in \real^{n \times m}$**

**Query  matrix $Q\in \real^{n \times h_d }$ is collection of query vectors one for each token** 

**Query weight matrix $W^Q\in \real^{m\times h}$**

***Note: Similary we calculate Key matrix $K$ , Value Matrix $V$ by using $W^K$ and $W^V$***

After we calculate the K, Q, V we come to the main attention operation as shown below 

![Untitled](Attention%20is%20all%20you%20need%20a3c80a6b34f84e4395186ef8e892402d/Untitled%202.png)

After this we get the representation $Z$ of the input from the self-attention model. 

# Multi headed self attention

As we have seen in the self attention model we find a representation $Z$  of an inuput $X$ using three parameters $W^Q,W^K,W^V$

So the total number of self attention model parameters = $W^Q + W^K + W^V$

where each $W \in \real^{m \times h}$

So total paramters = $3 \times m \times h$

Now to get even a better representation we get multi headed attention we increase the number of parameters by using multiple self attention heads sequentially as shown in the figure below 

![Untitled](Attention%20is%20all%20you%20need%20a3c80a6b34f84e4395186ef8e892402d/Untitled%203.png)

Here we learn an additional matrix $W^O$ which is used to combine the representations from different heads into a single representation $Z$ at the end 

So the number of parameters = $3 \times m \times h \times n_h + n_h \times h \times o$

where $o$ is the output vector size 

and $n_h$ is the number of heads 

# Encoder