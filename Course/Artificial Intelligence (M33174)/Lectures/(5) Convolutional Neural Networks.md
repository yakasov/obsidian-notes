The normal approach for image handling in the context of neural networks is to stretch the image into a single dimensional array, then calculate the weights required and multiply each element of the input by a row of the weight matrix $W$ to get the output.

This method has the side effect of distorting the input - it is a new dimension, instead of being preserved in its original form.

In order to preserve the spatial structure of the original image, we can use a "filter". For example, if we have a 32x32x3 image, we can convolve the filter with the image. Our filter must always extend the full depth of the input volume.

This gives us our convolution layer as seen below.
![[Pasted image 20231202160041.png]]

In order to work with our filter $W$, we need to stretch it out, stretch the input volume it's laid over, and then take the dot product. In essence, we stretch the input and the filter out in vector forms. $W$ is transposed because we need our dot products to be different (eg 1x75 $\cdot$ 75x1, not 1x75 $\cdot$ 1x75)

![[Pasted image 20231202160326.png]]

If we have multiple filters (for example, 6 5x5 filters) we will end up with 6 separate activation maps.
![[Pasted image 20231202160403.png]]
We can stack these up to get a "new image" size of 28x28x6!

![[Pasted image 20231202160938.png]]
![[Pasted image 20231202160944.png]]

We call the layers convolutional because it is related to the convolution of two signals: $$f[x, y] \times g[x, y] = \sum_{n_1 = -\infty}^{\infty} \sum_{n_2 -\infty}^{\infty}f[n_1, n_2] \cdot g[x - n_1, y - n_2]$$
#### A closer look at spatial dimensions
![[Pasted image 20231202162004.png]]
![[Pasted image 20231202162011.png]]
If we were to move the green 3x3 along to the right, we would have 5 different positions it could be in - this gives us 5 values. In total, we have a 5x5 output.

We can choose to jump every 2 pixels. This is called a stride, so our stride = 2. With a stride of 2, we have an output size of 3x3.

Our output size is equal to$$(N - F)\: \div \: \text{stride} + 1$$where $N$ is the height/width of the bounds, and $F$ is the height/width of our filter.

In practise, it is common to zero pad the border.![[Pasted image 20231202162302.png]]
With a stride of 1, this would give us an output of 7x7.

In general, stride = 1, filters are square ($F \times F$), and zero-padding follows the rule $(F - 1) \: \div \: 2$ (to preserve size spatially).

Applying multiple filters make look similar to the below.
![[Pasted image 20231202162435.png]]

> [!faq] Example
> If we have an input of $32 \times 32 \times 3$, with 8 $5 \times 5$ filters with stride 1 and padding 2, then:
> - output size: $((32 + (2 \times 2)) - 5) \:\div\: 1 + 1 = 32$ spatially, so $32 \times 32 \times 8$
> - parameters in layer: $5 \times 5 \times 3 + 1 = 76$ (where the $+1$ is our bias) results in $8 \times 76 = 608$


### Summary
A convolutional layer:
- accepts an image of size $W_1 \times H_1 \times D_1$
- needs 4 parameters defined:
	- number of filters, $K$
	- dimension of filters, $F$
	- stride (step), $S$
	- zero padding, $P$
- the output is:
	- an output of size $W_2 \times H_2 \times D_2$
	- $W_2 = (W_1 - F + 2P) \:\div\: S + 1$
	- $H_2 = (H_1 - F + 2P) \:\div\: S + 1$
	- $D_2 = K$

This means we get $F \times F \times D_1$ weights per filter (or $F \times F \times D_1) \times K$ total weights (plus as many biases). In general, $K$ is usually a power of 2.

### ReLU (activation) function
In reality, Sigmoid isn't used much for convoluted neural networks - instead, ReLU is preferred (and is very popular in deep learning). ReLU stands for Rectified Linear Unit:

**Function:** $\begin{aligned}(x)^+ &= \begin{cases}0 \:\text{if}\: x \leq 0 \\ 1 \:\text{if}\: x \gt 0 \end{cases} \\ &= \max(0, x) = x1_{x \gt 0}\end{aligned}$ 
**Derivative:** $\begin{cases}0 \:\text{if}\: x \lt 0 \\ 1 \:\text{if}\: x \gt 0 \end{cases}$ 
**Bounds:** $[0, \infty)$ 

In programming terms, 
```
if input > 0:
	return input
else:
	return 0
```

### Pooling layer
A pooling layer effectively down samples the input, usually by about half. We usually the MAX pooling approach.
![[Pasted image 20231202163744.png]]

#### MAX Pooling
![[Pasted image 20231202163803.png]]
**Input:** $W_1 \times H_1 \times D_1$ 
**Parameters:** 
- size of Pooling filter, $F_p$
- stride, $S_p$ 
**Output:** $W_2 \times H_2 \times D_2$ 
where
- $W_2 = (W_1 - F_p) \:\div\: S_p + 1$
- $H_2 = (H_1 - F_p) \:\div\: S_p + 1$
- $D_2 = D_1$

The final layer is a usual fully connected layer.
