# Cracking_code_using_RNN_at-character_level
Decipher encrypted strings with various simple recurrent neural networks


In this notebook, we'll look at how to build a recurrent neural network and train it to decipher strings encrypted with a certain cipher.

# Description

Machine Translation can be thought of as a sequence-to-sequence learning problem.
You have one sequence going in, i.e. a sentence in the source language, and one sequence coming out, its translation in the target language.
This seems like a very hard problem - and it is! But recent advances in Recurrent Neural Networks have shown a lot of improvement. A typical approach is to use a recurrent layer to encode the meaning of the sentence by processing the words in a sequence, and then either use a dense or fully-connected layer to produce the output, or use another decoding layer.
Experimenting with different network architectures and recurrent layer units (such as LSTMs, GRUs, etc.), you can come up with a fairly simple model that performs decently well on small-to-medium size datasets. Commercial-grade translation systems need to deal with a much larger vocabulary, and hence have to use a much more complex model, apply different optimizations, etc. Training such models requires a lot of data and compute time.
