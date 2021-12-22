# Some definitions:  

<b>Transfer learning</b> is the process of applying knowledge gained from one task to a separate yet related task.  

<b>Catastrophic forgetting</b> is a deleterious event that can occur within a trained neural net during fine-tuning. It occurs when important parameters within the network are changed to fit the new data, compromising the network’s ability to handle the old data.  

# Progressive networks  
Prognets begin their existence with just a single column neural net which will be trained on an initial task. Every column is made of L blocks, each including a layer of neurons W, a set of lateral neurons for each parent column U, and an activation function f. As the initial column has no incoming lateral connections, it will act identically to a standard neural network. This first column learns task 1, and then its parameters are frozen. For task 2, a new column is generated and lateral connections are added. These lateral connections take as input the outputs of the previous block in all prior columns. The lateral layers are then added to the main layer and finally the activation is applied.
- dimensionality reduction:  h(:k)i–1 denotes the concatenated features from all networks j < k. Similarly, for each network, one α(j)i is learned to scale the features (note that the notation above would imply a element-wise multiplication of the α(j)i's repeated in a vector, or equivalently a matrix-vector product). V(k)i then describes a dimensionality reduction; overall, a one-layer perceptron is used to “transfer” features from networks j < k to the current network. The same approach can also be applied to convolutional layers (e.g. a 1×1 convolution can be used for dimensionality reduction).

## Cons:  
- parameter-wasteful: each lateralized block requires a full lateral layer for each parent column it draws from

# Experiments  
- Pong variants, labyrinth variants, and Atari games  
