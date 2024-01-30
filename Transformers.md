## In comparison to Recurrent Neural Networks (RNN)
RNNs weren't very good at 
- handling large amounts of text
	- at the end of a paragraph they'd forget what happened at the beginning

Transformers were initially made to translate language

## Advantages 
They can be easily parallelized so they can be trained on a lot more data

## Innovations
1. Positional encoding
	- store information about the word order in the data instead of in the structure of the network
2. Attention
	- allows the model to focus on different parts of the input sequence when processing information
3. Self-attention
	- the model creates representations of each word by considering its relationship with all other words in the sequence

