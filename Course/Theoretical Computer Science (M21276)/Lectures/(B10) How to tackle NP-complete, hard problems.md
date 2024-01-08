If we can identify that our problem is $\mathcal{NP}$-complete (or $\mathcal{NP}$-hard), we know it's not worth looking for an optimal solution. We can then spend our time looking for a solution which may not be ideal, but which works well enough anyway.

### Heuristic approach
An algorithm that works "reasonably well" for many instances, but for which there is no proof that the algorithm is always "fast" or always produces a "good" solution. 

Examples:
- genetic algorithms
- greedy colouring algorithm for the graph colouring problem
- nearest neighbour algorithm for TSP

> [!faq] Example for the colouring problem
> Input: a graph $G$
> Output: a minimum number $k$ such that $G$ is $k$-colourable
> 
> The problem is $\mathcal{NP}$-hard, the decision version is $\mathcal{NP}$-complete
> 
> Algorithm:
> - order the vertices $v_1, ..., v_n$ of $G$;
> - for each $i$ from 1 to $n$ assign to $v_1$ the smallest available colour not used by $v_i$'s neighbours among $v_1, ..., v_{n-1}$ adding a new colour if needed
> 
> ![[Pasted image 20231212100438.png]]


### Approximation algorithm approach
An algorithm which finds in polynomial time a solution that is "close" to the optimal solution for every instance (and there is a proof for all these properties).

"Close" can have different meanings - it could mean arbitrarily close to the optimal solution, e.g. $1 + \varepsilon$ for any $\varepsilon$, or differ by a constant factor, or even worse.

For example, $r$-approximation $\mathcal{A}$ for a minimisation problem $M$ means $\mathcal{A}$ is a polynomial time algorithm which for any instance $M$ returns a solution at most $r$-times larger than an optimal one ($r \gt 0$ is a constant).

##### Approximation algorithms for metric TSP
Metric TSP - distance on the edges correspond to the Euclidean distances - TSP with triangle inequality
$d(A, B) + d(B, C) \geq d(A, C)$ 

> [!faq] Example
> If the distance measure is a metric and symmetric, there is a known 3/2-approximation algorithm for the travelling salesman problem.

This means that for any instance of the TSP with the distance measure being a metric and symmetric, there exists a polynomial time algorithm which returns a solution at most 1.5 times larger than the optimal one (never more than 150% of the optimum).

The construction of that solution is based on a solution of the Minimum Spanning Tree.
- find the minimum spanning tree (MST) of the graph with $n$ vertices
  the MST is a connected subgraph of the graph with all vertices and the total sum of the edges in the tree is minimal from all connected subgraphs with such properties
- an $O(n^2\log{n})$ algorithm exists to compute the MST
- duplicate all the edges of MST. This gives us an Eulerian graph. We then need to find a Eulerian cycle in it.
  ![[Pasted image 20231212101333.png]]
- walk along the Eulerian cycle, and each time you are about to come into an already visited vertex, skip it and try to go to the next one (along the Eulerian cycle)
  ![[Pasted image 20231212101400.png]]
  The result is a TSP tour no more than twice as long as the optimal one! It can further be improved to a tour of length at most 1.5 times the shortest tour.

### Restriction approach
Some $\mathcal{NP}$-hard/$\mathcal{NP}$-complete problems can be in $\mathcal{P}$, when we solve them only for a subset of all instances.
- the 3-satisfiability problem is $\mathcal{NP}$-complete, but 1- or 2-satisfiability problem is in $\mathcal{P}$
- the $k$-colouring problem is in $\mathcal{P}$ for trees, bipartite graphs, etc. - in fact many $\mathcal{NP}$-hard graph optimisation problems are in $\mathcal{P}$ for a class of trees
- for the timetabling problem there are polynomial solutions in the case when there are less than three subjects

### Parametrisation
Often there are fast algorithms if certain parameters are fixed or have a small value.

> [!faq] Example
> Input: a graph $G$, an integer $k$
> Output: does $G$ have a vertex cover of size at most $k$?
> 
> The problem is $\mathcal{NP}$-hard, the decision version is $\mathcal{NP}$-complete
> - the running time of a brute-force algorithm is $O(kn(\begin{array}{} n \\ k\end{array})) = O(kn^{k+1})$
> - but there is also an algorithm whose running time is exponential in $k$ but polynomial in $n$, e.g. $O(2^kn)$
> 
> If a graph has a small vertex cover, it cannot have too many edges - if $G$ has $n$ vertices and $G$ has a vertex cover of size at most $k$, then $G$ has at most $kn$ edges. We can return NO if $G \gt kn$ edges.
> 
> Consider an edge $(u, v)$. Either $u$ or $v$ must be in the vertex cover.
> 
> $G$ has a vertex cover of size at most $k$ if for any edge $(u, v)$ either $G \backslash \{u\}$ or $G \backslash \{v\}$ has a vertex cover of size at most $k - 1$. $G \backslash \{u\}$ is the graph $G$ without vertex $u$ and the edges incident with $u$.

### Probabilistic polynomial algorithm approach
This is an algorithm which is usually correct in all but a very small number of cases.

> [!faq] Example
> One important problem that has such an algorithm is the primeness problem. It is based on the selection of $k$ random numbers between $1$ and $n - 1$, where $n$ is the number to be tested for primeness:
> - if $n$ is prime the algorithm returns YES
> - if $n$ is not prime, then there is a small probability that the algorithm will return YES instead of NO. This probability is less than $\frac{1}{2^k}$

For example:
- choose a number $a \lt n$
- check some equality (corresponding to the chosen test) involving $a$ and the given number $n$. If the equality fails to hold true, then $n$ is a composite number, $a$ is a witness for the compositeness, and the test stops.
- repeat from step 1 until the required accuracy is achieved
After one or more iterations, if $n$ is not found to be a composite number, then it can be declared *probably* prime.