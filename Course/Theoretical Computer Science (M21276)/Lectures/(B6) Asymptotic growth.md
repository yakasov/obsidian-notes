### Overview
- to calculate $T(n)$, we must find how many times the most expensive operations are called
- for the worst case time complexity, an algorithm must take at most $T(n)$ steps for all inputs of length $n$
- our plan is to understand which algorithm is better and explore some methods for the analysis of algorithmic efficiency - our focus is on time efficiency

$$\text{for $x \geq 4$,} \: n^n \gt n! \gt 2^n \gt n^2 \gt n\log n \gt n \gt \log n \gt 1$$

### Asymptotic analysis of an algorithm
> [!info] Example
> If the algorithm $A$ has the time complexity $T_A(n) = n + 10$ and the algorithm $B$ has $T_B(n) = n$, then asymptotic growth of both functions is the same $n$, so $n \sim n + 10$.

> [!info] Example
> If $T_A(n) = 4n^2 + 3n + 10$ and $T_B(n) = 2n^2$, then asymptotic growth of both functions is the same $n^2$, so $4n^2 + 3n + 10 \sim 2n^2 \sim n^2$.

Essentially, we look at the running time of an algorithm when the input size $n$ is large enough so that constants and lower-order terms do not matter.

#### Asymptotic behaviour of functions
We want to express the rate of growth of a function:
- the dominant term with respect to $n$,
- ignoring constants in front of it
$$\begin{aligned} k_1n + k_2 &\sim n \\ k_1n\log n &\sim n\log n \\ k_1n^2 + k_2n + k_3 &\sim n^2 \end{aligned}$$
We also want to formalise that, for example, an $n\log n$ algorithm is better than an $n^2$ algorithm

### Big O...
$O(...)$ is called an asymptotic upper bound of a function.

**Informally:** when $f, g$ are two non-negative functions then $f(n)$ is $O(g(n))$ if $f$ grows at most as fast as $g$.
**Formally:** $f(n) = O(g(n))$ if there exists $c, n_0 \in \mathbb{R}^+$ such that for all $n \geq n_0, f(n) \leq c \times g(n)$.

When we write $$f(n) = O(g(n)) \:\text{or}\: f(n) \in O(g(n))$$we read it as "$f(n)$ is big O of $g(n)$".

> [!info] Example
> $\frac{1}{3}n^2 - 3n = O(n^2)$ because $$\frac{1}{3}n^2 - 3n \leq cn^2 \:\text{if}\: c \geq \frac{1}{3} - \frac{3}{n}$$ which is true if $c = \frac{1}{3}$ and $n \geq 1$.

> [!info] Example
> $O()$ gives an upper bound on $f$, but not necessarily a tight one: $$n = O(n), 3n = O(n^2), 7n = O(n^3), n = O(n^{100})$$

#### Big Omega ($\Omega$-notation)...
$\Omega(...)$ is called an asymptotic lower bound of a function.

**Informally:** when $f, g$ are two functions then $f(n)$ is $\Omega(g(n))$ if $f$ grows at least as fast as $g$.
Formally: $f(n) = \Omega(g(n))$ if there exists $c, n_0 \in \mathbb{R}^+$ such that for all $n \geq n_0, f(n) \geq c \times g(n)$.

When we write $$f(n) = \Omega(g(n)) \:\text{or}\: f(n) \in \Omega(g(n))$$we read it as "$f(n)$ is big omega of $g(n)$".

> [!info] Example
> $4n^2 - 10 = \Omega(n^2)$, because $f(n) = 4n^2 - 10$ and $n^2 \leq 4n^2 - 10$ for all $n \geq 2$, hence $c = 1$ and $n_0 = 2$.

Like $O(), \Omega()$ gives a lower bound on $f$, but not necessarily a tight one.

#### Big Theta ($\Theta$-notation)...
$\Theta(...)$ is used to denote the asymptotic tight bound of a function.

**Informally:** when $f, g$ are functions then $f(n)$ is $\Theta(g(n))$ if $f$ is essentially the same as $g$, to within a constant multiple.
**Formally:** $f(n) = \Theta(g(n))$ if $f(n) = O(g(n))$ and $f(n) = \Omega(g(n))$, i.e there exist $n_0, c_1, c_2 \in \mathbb{R}^+$ such that for all $n \geq n_0, c_1 \times g(n) \leq f(n) \leq c_2 \times g(n)$.

When we write $$f(n) = \Theta(g(n)) \:\text{or}\: f(n) \in \Theta(g(n))$$we read it as "$f(n)$ is big theta of $g(n)$".

> [!info] Example
> $4n^2 - 10 = \Omega(n^2)$ and $4n^2 - 10 = O(n^2)$ which means $4n^2 - 10 = \Theta(n^2)$.

But $$n \neq \Theta(n^2), \: n^2 + 3n \neq \Theta(n^3), \: \log n \neq \Theta(n)$$
#### Comparing $T(n)$
Another important notation: $f(n) \prec g(n)$ if $$f(n) = O(g(n)) \: \text{and} \: f(n) \neq \Theta(g(n))$$
Here is a hierarchy of some familiar functions according to their growth rates: $$1 \prec \log n \prec n \prec n \log n \prec n^2 \prec n^3 \prec 2^n \prec 3^n \prec n! \prec n^n$$
#### Calculating $T(n)$
Calculating the time complexity $T(n)$ is often very difficult, there are lots of different techniques. When analysing an algorithm, we might need to estimate the complexity of sum, and their complexities are as follows:
$$\begin{aligned} \sum^n_{i=1}i &= \Theta(n^2) \\ \sum^n_{i=1}i^2 &= \Theta(n^3) \\ \sum^n_{i=1}i^k &= \Theta(n^{k+1}) \\ \log n! &= \Theta(n \log n) \end{aligned}$$
![[Pasted image 20231128103508.png]]

From the table, we can see that exponential time is bad, whereas polynomial is better.

#### Tractable and intractable problems
##### Tractable Problems
A problem that is solvable by a polynomial-time algorithm.

Examples:
- searching an unordered/ordered list
- sorting a list of numbers
- multiplication of two matrices
- finding a minimum spanning tree in a weighted graph (Kruskal, Prim)
- finding a Eulerian circuit in a graph (a circuit using each edge)
- finding the shortest path between any two vertices in a graph (Dijkstra)

##### Intractable Problems
There is not a known polynomial time algorithm:
- for some problems, there is a proof that a polynomial algorithm doesn't exist
- for some problems, nobody has been able to prove it so far

Examples:
- traveling salesman problem
- Tower of Hanoi
- finding a Hamiltonian cycle in a graph (a cycle using each vertex)
- finding the longest path between any two vertices in a graph

### Summary
- with big $\Theta$, big O and big $\Omega$, we know how to compare these functions at the limit where the input is very large
- polynomial algorithms $\gt$ exponential algorithms
- tractable and intractable problems