##### Basic Points
Brains can:
- recognise images/objects/abstract symbolic information
- retrieve information based on partial descriptions
- organise information

Computers can:
- do arithmetic and arithmetic logic
- deductive logic
- retrieve information based on arbitrary features

> put rosenblatt's artificial neurone image here

##### Perceptron
A perceptron is an algorithm for supervised learning of binary classifiers. This algorithm enables neurones to learn and process elements in the training set one at a time.

> put the new artificial neurone image here (w constant, inputs -> weights -> weighted sum -> step function -> out)

A perceptron is a neural network composed of a single layer feed-forward network using threshold activation functions. Feed-forward means that all the interconnections between the layers propagate forward to the next layer.

The simple perceptron uses the threshold activation function with a bias and thus has a binary output. The binary output perceptron has two possible outputs: 0 and 1. It is trained by supervised learning and can only classify input patterns that are linearly separable.

Training is accomplished by initialising the weights and bias to small random values and then presenting input data to the network. The output ($y$) is compared to the target output ($t = 0$ or $t = 1$), and the weights are adapted according to Hebb's training rule.

The simple single layer perceptron can separate linearly separable inputs but will fail if the inputs are otherwise. One such example of linearly non-separable inputs is the exclusive-or (XOR) problem. Linearly non-separable patterns, such as those of the XOR problem, can be separated with multilayer networks.

> [!Definition] Limitations Summary
> Perceptrons are limited in that they can only separate linearly separable patterns and that they only have a binary output.

Many of the limitations of the simple perceptron can be solved with multi-layer architectures, non-binary activation functions, and more complex training algorithms.

##### Multiple Perceptron
Multilayer perceptrons with threshold activation functions are not that useful because they can't be trained with the perceptron learning rule and since the functions are not differentiable, they can't be trained with gradient descent algorithms.

###### Activation Functions
The activate function is generally non-linear. Linear functions are limited because the output is simply proportional to the input.
![[Pasted image 20231030172857.png]]

![[Pasted image 20231030173051.png]]
*Multilayer architecture*

##### Feedforward Neural Networks
The basic structure of a feedforward neural network is as follows:
![[Pasted image 20231030173803.png|test]]
The learning rule modifies the weights according to the input the patterns are presented with. In a sense, ANNs learn by example as do their biological counterparts.

When the desired outputs are known we have supervised learning or learning with a teacher.
![[Pasted image 20231030174005.png]]
*Multiple layers in the feedforward network*

##### Overview of the back-propagation
1. a set of examples for training the network is assembled. Each case consists of a problem statement (which represents the input into the network) and the corresponding solution (which represents the desired output from the network).
2. the input data is entered into the network via the input layer.
3. each neurone in the network processes the input data with the resultant values steadily "percolating"
> more stuff here from pic

##### The Learning Rule
> even more stuff here from another pic im lazy


> assume all this will be uploaded hopefully :^)