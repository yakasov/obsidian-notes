### Image Classification
Image classification works by taking an input image and outputting a category to assign the image to (for example, assigning an image of a cat to the category Cat).

However, there are certain challenges that image recognition faces, such as:
- **Viewpoint:** if the input image is not a clear view of the cat
- **Illumination:** if the image lighting differs drastically or is too bright/dark
- **Deformation:** the shape of the cat may not be consistent (like a cat posing or lying down)
- **Occlusion:** if part of the cat is hidden behind something
- **Clutter:** if the cat is camouflaged in the surroundings 
- **Intraclass Variation:** different cats look different (like different patterns on the fur)

### Linear Classifiers
Linear classifiers are relatively simple, but can be used as the building blocks for larger neural networks.

#### Parametric Approach
![[Pasted image 20231202150537.png]]
In this approach, our top function is equal to $f(x, W) = Wx + b$, which, for the above example, can be equated to: $$(10,) = (10, 3072) \times (3072,) + (10,)$$ (where $W$ is our parameters or weights)

![[Pasted image 20231202150953.png]]
From an algebraic viewpoint, we can see our input image as a stretched column of pixels. For example, we might change an image into one long column of pixels in a line.

Instead of having our $b$ bias separately, we can absorb the bias into the last column of the weight matrix provided we add an extra one to the data vector: $$\underbrace{\begin{bmatrix} 0.2 & -0.5 & 0.1 & 2.0 & | & 1.1 \\ 1.5 & 1.3 & 2.1 & 0.0 & | & 3.2 \\ 0 & 0.25 & 0.2 & -0.3 & | & -1.2 \end{bmatrix}}_{W (3, 5)} \rightarrow \underbrace{\begin{bmatrix} 56 \\ 231 \\ 24 \\ 2 \\ 1 \end{bmatrix}}_{(5,)} = \underbrace{\begin{bmatrix} -96.8 \\ 437.9 \\ 61.95 \end{bmatrix}}_{(3,)}$$
With linear classifiers, predictions are also linear, meaning: $$\begin{split} f(x, W) &= Wx \:\text{(ignore bias)} \\ f(cx, W) &= W(cx) = c \times f(x, W) \end{split}$$ ![[Pasted image 20231202152142.png]]

#### Visual viewpoint
![[Pasted image 20231202152334.png]]
This approach can work, but has limitations. A template cannot be applied to multiple different versions of the data (for example, a car from many angles, or a dog partially obscured, etc). We can only have one template per category.

#### Geometric viewpoint
![[Pasted image 20231202152630.png]]
As we look at different areas and compare them to the templates, the scores for each template will change. This can also be seen as hyperplanes carving up a high-dimensional space.
![[Pasted image 20231202152702.png]]

#### Hard cases for a Linear Classifier
![[Pasted image 20231202152824.png]]
Remember that the perceptron cannot be applied to XOR problems!

So far, we've defined a linear score function of $f(x, W) = Wx + b$, so for a given $W$ we can compute the class scores for an image $x$.

But how can we choose a good $W$?

### Loss functions
In order to choose a good $W$, we can:
1. use a **loss function** to quantify how good a value of $W$ is
2. find a $W$ that minimises the loss function (**optimisation**)

A loss function is a metric that can tell us how good the system performs. Low loss means better performance than high loss. Loss functions are also known as cost or objective functions.

There are also exists negative loss functions, also known as reward, profit or fitness functions.

Given a dataset of examples $$\{(x_i, y_i)\}\begin{array}{l}N \\ i=1 \end{array}$$where $x_i$ is the image and $y_i$ is the (integer label), our loss for a single example is $$L_i(f(x_i, W), y_i)$$and our loss for the dataset is the average of per-example losses $$L = \frac{1}{N}\sum_i L_i(f(x_i, W), y_i)$$
#### Support vector machines
The score of the correct class should be higher than all other scores.
![[Pasted image 20231202154816.png]]

Given an example ($x_i, y_i$) where $x_i$ is the image and $y_i$ is the label, if we let $s = f(x_i, W)$ be scores, then the SVM loss has the form $$L_i = {\sum}_{j \neq y_i}\max(0, s_j - s_{y_i} + 1)$$
For example data such as the below, ![[Pasted image 20231202155035.png]]
we can apply the formula to calculate the losses for each category:
- for 'cat', $$\begin{aligned}L_i &= \max(0, 5.1 - 3.2 + 1) + \max(0, -1.7 - 3.2 + 1) \\ &= \max(0, 2.9) + max(0, -3.9) \\ &= 2.9 + 0 \\ &= 2.9 \end{aligned}$$
- for 'car', $$\begin{aligned}L_i &= \max(0, 1.3 - 4.9 + 1) + \max(0, 2.0 - 4.9 + 1) \\ &= \max(0, -2.6) + max(0, -1.9) \\ &= 0 + 0 \\ &= 0 \end{aligned}$$
- for 'frog', $$\begin{aligned} L_i &= \max(0, 2.2 - (-3.1) + 1) + \max(0, 2.5 - (-3.1) + 1) \\ &= \max(0, 6.3) + \max(0, 6.6) \\ &= 6.3 + 6.6 \\ &= 12.9 \end{aligned}$$
We can finally calculate the loss over the dataset as the average of losses = 5.27

