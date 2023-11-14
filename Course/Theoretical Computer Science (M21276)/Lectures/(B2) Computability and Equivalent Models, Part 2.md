#### Model 5: Recursive functions
We only consider functions whose arguments and values are natural numbers.

The basic characteristic of a computable functions is that there must be a finite procedure (an algorithm) telling how to compute the function.

If the function is defined by expressions like $f(n) = n^3 + 1$, a recipe is given.

Church, along with Stephen Kleene and J.B. Rosser created a formal definition of a class of functions whose values could be calculated by recursion (partial recursive functions).

We believe that the functions of the following form are computable:
	$f(x) = 0$, $g(x) = x + 1$, and $h(x, y, z) = x$
Functions like these together with simple combining rules are all we need to construct all possible computable functions.

Unlike for Turing machines, the description of recursive functions is *inductive*.

**Overview:**
- we introduce the primitive recursive functions
- we introduce the recursive function by adding a construct called minimisation
- intuitively, primitive recursive functions can only do finite loops and always terminate, whereas minimisation corresponds to infinite loops

##### Motivation
Consider the function $\text{exp}(x, y) = x^y$:
	$x^0 = 1$
	$x^1 = x$
	$x^2 = x \cdot x$ 
	$...$
	$x^y = x \cdot x \cdot ... \cdot x$ ($y$ occurrences of $x$)
	$x^{y+1} = x \cdot x \cdot ... \cdot x$ ($y + 1$ occurrences of $x$)
	$= x \cdot x^y$
The two "rewriting rules" are enough to define the $\text{exp}$ function:
	$x^0 = 1$
	$x^{y+1} = x \cdot x^y$
So, the rules for $\text{exp}$ reduce exponentiation to multiplication.

Now consider *multiplication*:
	$x \cdot 0 = 0$
	$x \cdot (y + 1) = x + x \cdot y$
So the rules for $\cdot$ reduce multiplication to addition.

Now consider *addition*:
	$x + 0 = x$
	$x + (y  + 1) = (x + y) + 1$
So the rules for $+$ reduce addition to adding $1$.

Informally,
- primitive recursion is in the spirit of our "computation by rewriting" definitions of $\text{exp}, \cdot$ and $+$.
- if we want to use "recursion" it consists of one rule for $y = 0$ and one rule for $y \gt 0$;
  $y$ acts as a "countdown" for the number of remaining steps in the computation

Now we introduce the building blocks for primitive recursive functions. There will be
- three basis functions: *successor*, *zero*, and *projections*
- two ways of building new primitive recursive functions from old ones: *composition* and *primitive recursion*

##### Building blocks
1. the zero function: $\text{zero}: \mathbb{N} \rightarrow \mathbb{N}, \text{zero}(x) = 0$
2. the successor function: $\text{succ}(x) = x + 1$
3. the projection function: $\text{project}_i: \mathbb{N}^k \rightarrow \mathbb{N}$
   $\text{project}_i(x_1, ..., x_k) = x_i, i \in \{1, ..., k\}$

##### Rule 1: Composition
If $\text{g}_1, \text{g}_2, ..., \text{g}_m$ are functions of $\mathbb{N}^k \rightarrow \mathbb{N}$, and $\text{f}$ is a function $\mathbb{N}^m \rightarrow \mathbb{N}$, then the function $\text{h} : \mathbb{N}^k \rightarrow \mathbb{N}$ given by
	$\text{h}(x_1, ..., x_k) = \text{f}(\text{g}_1(x_1, ..., x_k), ..., \text{g}_m(x_1, ..., x_k))$
is said to arise by *composition* from $\text{f}, \text{g}_1, ..., \text{g}_m$.

Composition replaces the arguments of a function with other functions.

>[!faq] Example
>$\text{h}(x) = \text{succ}(\text{zero}(x))$
>$\text{h}(x)$ is the constant function that always returns $1$.


##### Rule 2: Primitive Recursion
Define a new function $\text{f}$ in terms of the function $\text{h}$ and $\text{g}$ as follows:
	$\text{f}(x_1, x_2, ..., x_n, 0) = \text{h}(x_1, x_2, ..., x_n)$,
	$\text{f}(x_1, x_2, ..., x_n, \text{succ}(y)) = \text{g}(x_1, x_2, ..., x_n, y, \text{f}(x_1, x_2, ..., x_n, y))$

> [!info] Definition
> A function is *primitive recursive* if it can be built up using the base functions and the operations of composition and primitive recursion.

> [!faq] Example 1
> **The function $\text{identity}(x) = x$ is a primitive recursive function. Why?**
> 	<p  class="tab"/>$\text{identity}(x) = \text{project}_1(x)$

> [!faq] Example 2
> **The constant function $\text{f}(x) = 1$ is a primitive recursive function. Why?**
> 	<p  class="tab"/>$\text{f}(x) = \text{succ}(\text{zero}(x))$
> 
> - base function
> - composition

>[!faq] Example 3
> **The function $\text{add}(x, y) = x + y$ is a primitive recursive function. Why?**
> First a recursive definition of addition:
> 	<p  class="tab"/>$\text{add}(x, 0) = x$,
> 	$\text{add}(x, \text{succ}(y)) = \text{succ}(\text{add}(x, y))$
> 
> Does it work? Yes! This gives a clear recipe:
> 	<p  class="tab"/>$\text{add}(2, 2) = \text{succ}(\text{add}(2, 1))$
> 	$= \text{succ}(\text{succ}(\text{add}(2, 0)))$
> 	$= \text{succ}(\text{succ}(2))$
> 	$= \text{succ}(3)$
> 	$= 4$
> 
> Is this a primitive recursive function?
> 	<p  class="tab"/>$\text{add}(x, 0) = x$,
> 	$\text{add}(x, \text{succ}(y)) = \text{succ}(\text{add}(x, y))$
> 
> Following the definition of primitive recursion we have to realise that the right side can be rewritten using primitive recursive functions:
> 	<p  class="tab"/>$\text{f}(x, 0) = \text{h}(x)$,
> 	$\text{f}(x, \text{succ}(y)) = \text{g}(x, y, \text{f}(x, y))$
> 
> So,
> 	<p  class="tab"/>$\text{h}(x) = x = \text{project}_1(x)$
> 	$\text{g}(x, y, u) = \text{succ}(u) = \text{succ}(\text{project}_3(x, y, u))$


finish these notes pls
