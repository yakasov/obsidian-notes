When solving a problem, the algorithm matters - we want fast algorithms that don't use a lot of memory or time (bounded resources).

### Bounds
#### Lower bound
For a lower bound $L(n)$ of an algorithm, it is not possible to have any other algorithm (for a common problem) whose time complexity is less than $L(n)$ for any input. Every algorithm must therefore take at least $L(n)$ time in the worst case.

Each better algorithm brings the upper bound downwards.

#### Upper bound
Inversely, the upper bound $U(n)$ of an algorithm is the worst case time taken. We can always solve the problem in at most $U(n)$ time.

Each better proof brings the lower bound upwards.


More often than not, we need to find the *problem complexity*, i.e the complexity of sorting or searching in general, rather than the *algorithm complexity*. However, a lot of the time we do not know the problem complexity, only that it has bounds.

#### Proofs of Lower bounds
Proofs of lower bounds are often tricky to find, which is why there are gaps for so many problems. 

A useful method for proving a lower bound $\log{n}$ for searching for an item $x$ in an ordered array $S$ of $n$ items is based on the decision trees. That method can also be used for solving other problems and proving a lower bound $n\log{n}$ for sorting.

The binary search algorithm has a complexity of $O(\log{n})$, so the complexity of the problem "searching an ordered list" is at most $O(\log{n})$ - using the decision trees it is already a lower bound for the problem.

#### Decision trees
A decision tree for an algorithm is a tree whose
- internal nodes represent decision points in the algorithm (a query)
- leaves represent possible outcomes (an output)

> [!faq] Example
> The guessing game where one person thinks of an animal (one of six possible, e.g. fish, frog, fly, spider, gnu, eagle) and the other person tries to figure it out with a series of yes/no questions. How many questions do we need?
> 
> The game can be modelled as a decision tree:
> ![[Pasted image 20240108121436 1.png]]
> Each internal node is labelled with a question and has two edges, "yes" or "no". At each internal node, the answer to the query tells us which node to visit next.
> Each leaf is labelled with an animal. When we reach a leaf, we output its label.

### Logarithms
The number of decisions is certainly a lower bound on the actual running time, which is good enough to prove a lower bound on the complexity of a problem. If a problem has $n$ different outputs, then obviously any decision tree must have at least $n$ leaves.

In a binary tree, the number of leaves in a tree of height $d$ is at most $2^d$. Thus, if every query has at most 2 possible answers, then $2^d \geq n$ and hence the height of the decision tree must be at least $\lceil \log_2n \rceil = \Omega(\log{n})$.


### Types of problem
So far we have decidable and undecidable problems:

#### Undecidable (decision) problems
It has been proved no algorithm can ever exist to return yes or no.
- the Halting problem
- the Post Correspondence problem
- Hilbert's Tenth problem
- the (unbounded) Tiling problem
- the total problem
Some of these problems are partially decidable (there is an algorithm which returns yes, but might never return no).

#### Decidable problems
1. **(Proven) intractable** - solvable but impractical
2. **(Apparently) intractable** - those which appear to be intractable, but which *could possibly* be tractable
3. **Tractable** - practically solvable

An example for a (proven) intractable problem might be the Tower of Hanoi, or finding all routes for the Traveling Salesman problem with length less than a given constant $B$.

An example for an (apparently) intractable problem might be the Hamiltonian Cycle problem, the Traveling Salesman problem in general, the bounded tiling problem, or the Minimum Colouring problem.

An example for a tractable problem might be sorting, matrix multiplication, the Minimum Spanning Tree problem, deciding whether a  graph is Eulerian, or finding the shortest path between two vertices in a graph.

![[Pasted image 20240108123134 1.png]]