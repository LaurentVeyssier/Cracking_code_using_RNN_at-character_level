# Cracking_code_using_RNN_at-character_level
Decipher encrypted strings with various simple recurrent neural networks


In this notebook, we'll look at how to build a recurrent neural network and train it to decipher strings encrypted with a certain cipher.
Although this problem is a real simple one (know as Caesar cipher), it illustrates how a recurrent Neural Network (RNN) works and what kind of task it performs using sequence of data (text, time and other series). For example, RNN can be used for time-serie data forecasting.

# Description

Machine Translation can be thought of as a sequence-to-sequence learning problem. You have one sequence going in, i.e. a sentence in the source language, and one sequence coming out, its translation in the target language. This seems like a very hard problem - and it is! But recent advances in Recurrent Neural Networks have shown a lot of improvement. 

A typical approach is to use a recurrent layer to encode the meaning of the sentence by processing the words in a sequence, and then either use a dense or fully-connected layer to produce the output, or use another decoding layer. Experimenting with different network architectures and recurrent layer units (such as LSTMs, GRUs, etc.), one can come up with a fairly simple model that performs decently well on small-to-medium size datasets. Commercial-grade translation systems need to deal with a much larger vocabulary, and hence have to use a much more complex model, apply different optimizations, etc. Training such models requires a lot of data and compute time.

This project uses a character-level RNN model since the cipher works on the characer level. In a machine translation scenario, a word-level RNN is the more common choice.

A character-level RNN will take as input an integer referring to a specific character and output another integer which we can cover back to a character. By providing a training set of encryted sentences and their corresponding "clear" versions, the model will learn how to decode and translate back to plain text.

# Approach and tested models

For a neural network to predict on text data, it first has to be turned into data it can understand. Since a neural network involves a series of multiplication and addition operations, the input data needs to be numbers. Preprocessing of the input text is therefore necessary to get the model to work. Key preprocessing steps are :
- Isolating each character (instead of an entire phrase, or word being the element)
- Tokenizing the characters so we can turn them from letters to integers and vice-versa
- Padding the strings so that all the inputs and outputs have similar sequence length. This allows to fit the data into matrix form and benefit from the matrix computation capabilities of the machine

Different models are tested on this simple encryption case.
- Simple RNN cells.
- One layer LSTM (Long-Short-Time-Memory)
- One layer GRU (Gated Recurrent Unit), a simplified, but effective, version of LSTM cell

By default, the output of a RNN layer contains a single vector per input sequence (an encoded sentence). This vector is the RNN cell output capturing what the model identifies as important information from the input sequence. This vector corresponds to the last timestep (of the sequence), containing information about the entire input sequence. The shape of this output is (batch_size, units) where units corresponds to the units argument passed to the layer's constructor.

A RNN layer can also return the entire sequence of outputs for each sample (one vector per timestep per sample). This is what the projects uses (return_sequences=True). The shape of this output is (batch_size, timesteps, units).

The models are ending with a Dense layer which role is to generate a probability distribution over the possible output characters. The "translated" character can be identified from this probalility output.

# Results

Overall:

- the GRU has the least errors (only 1) but required higher training time with 16 epochs for 128 batch size
- SimpleRNN with the same training has much more errors
- Finally LSTM has 2 errors only and was trained with only 4 epochs and 64 batch size which is twice as less as the GRU

Conclusion: best performance for LSTM with GRU next

