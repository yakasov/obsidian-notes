### $\mathcal{P}$ and $\mathcal{NP}$ 
#### Class $\mathcal{P}$ 
- $\mathcal{P}$ is the set of all decision problems that can be solved by polynomial-time algorithms (tractable decision problems)
- To prove a problem is in $\mathcal{P}$ you must write a polynomial time algorithm to solve it

Examples:
- decide whether the maximum of $n$ integers is larger than a given constant
- decide whether a graph is an Eulerian graph


#### Class $\mathcal{NP}$
- $\mathcal{NP}$ is the set of all decision problems that can be solved by non-deterministic algorithms in polynomial time (apparently intractable decision problems)
- To prove a problem is in $\mathcal{NP}$ you must write a polynomial algorithm to verify whether a given certificate (a solution) is the proof (evidence) that the answer is 'yes'

Examples:
- Input: a graph $G$, a constant $k \in \mathbb{N}$ 
   Output: YES, if there exists a tour in the Traveling Salesman Problem of length at most $k$
- decide whether a given graph has a Hamiltonian cycle

Everything in $\mathcal{P}$ is in $\mathcal{NP}$! Equivalently, $$\mathcal{P} \subseteq \mathcal{NP}$$since to be in $\mathcal{P}$ - the problem must be solvable in polynomial time by a deterministic TM, which is also obviously a non-deterministic TM.

We currently don't know
- if there is a problem in $\mathcal{NP}$ which is definitely not in $\mathcal{P}$
- if all problems in $\mathcal{NP}$ are also in $\mathcal{P}$

#### The satisfiability problem
In 1971, Cook discovered that a number of problems were among the hardest in $\mathcal{NP}$, so called $\mathcal{NP}$-complete problems.

**The satisfiability problem:** given a Boolean expression written using only AND, OR, NOT, variables and parentheses. Is there an assignment of TRUE/FALSE values to the variables that makes the entire expression TRUE?

Every such Boolean expression is equivalent to the one in conjunctive normal form (CNF): a conjunction (AND) of only OR clauses, so we focus only on those.

> [!faq] Example
> $$(x \vee y \vee \neg{z}) \wedge (x \vee z)$$ is satisfiable by letting $x$ = TRUE, $y$ = FALSE, and $z$ = FALSE. But $$(x \vee y) \wedge (x \vee \neg{y}) \wedge \neg{x}$$ is not satisfiable because it is false for any assignment of truth values to $x$ and $y$.

The problem is in NP:
Let the length of an expression $n$ be the total number of literals that appear in it
$\implies$ the number of distinct variables in the expression is at most $n$
$\implies$ checking stage can be done in $O(n)$ time

Cook also proved that a restricted form of CNF-satisfiability - the 3-satisfiability problem is $\mathcal{NP}$-complete.

In the 3-satisfiability problem the expressions contain at most three literals in each OR clause.

### The importance of $\mathcal{NP}$-complete problems
- $\mathcal{NP}$-complete problems are all effectively equivalent in the sense that if any one of them is in $\mathcal{P}$, then they all are
- If any $\mathcal{NP}$-complete problem is ever shown to have a polynomial algorithm we could deduce $\mathcal{P} = \mathcal{NP}$

As of today, there are well over 1,000 problems known to be $\mathcal{NP}$-complete.

Some examples of $\mathcal{NP}$-complete problems:
- the graph colouring problem
- the Steiner Tree problem
- the CNF-satisfiability problem (also 3-satisfiability)
- the Traveling Salesman problem
- the Hamiltonian cycle problem
- Tetris, Minesweeper, the 15 puzzle
- timetabling decision problem

Any $\mathcal{NP}$-problem can be solved by an exponential algorithm, but for none of them a polynomial algorithm is known. Moreover no-one has been able to prove that no polynomial algorithm exists for any of those problems.

#### Definition of $\mathcal{NP}$-complete problem
A decision problem $B$ is $\mathcal{NP}$-complete if:
- $B \in \mathcal{NP}$,
- $A \leq B$ for all problems $A \in \mathcal{NP}$ i.e $\mathcal{NP}$-complete problems are problems in $\mathcal{NP}$ to which all other $\mathcal{NP}$ problems can be reduced in polynomial time

To prove a problem is $\mathcal{NP}$-complete:
- we must prove that our problem is in $\mathcal{NP}$
- we must find an $\mathcal{NP}$-complete problem $A$ that can be polynomially reduced to our problem

#### Polynomial reduction
Given two problems, a polynomial-time reduction is an algorithm that runs in polynomial time and reduces one problem to the other.

> [!faq] Example
> Given:
> - $A$: the 3-SAT problem
> - $B$: the decision version of TSP
> 
> We need to find a polynomial reduction which transforms an input $I_A$ of $A$ to the input $I_B$ of $B$ in such a way that $B$'s answer to $I_B$ is precisely $A$'s answer to $I_A$
> 
> - $I_A$ is an instance of $\mathcal{A} \rightsquigarrow I_B$ is an instance of $\mathcal{B}$
> - $I_A$ is YES instance $\Leftrightarrow$ $I_B$ is YES instance
> 
> For any formula $I_A$ we need to construct (in polynomial time) an instance $I_B$ of TSP (a weighted graph and the length of the tour) such that $I_A$ is satisfiable $\Leftrightarrow$ $I_B$ has a solution.
> 
> Then if we have an input $I_A$ to problem $A \Leftarrow$ we can transform $I_A$ into an input $I_B$ for problem $B$ and use our algorithm for $B$. 
> 
> If $B$ would have a polynomial algorithm, then we would have a polynomial algorithm for $A$ as well.

#### Between $\mathcal{P}$ and $\mathcal{NP}$
**The factorisation decision problem:** given an integer $n$ and an integer $m$ with $1 \leq m \leq n$, does $n$ have a factor $d$ with $1 \lt d \lt m$?

Nobody has ever been able to convert the satisfiability (or any other $\mathcal{NP}$-complete problem) to the factorisation problem, which is clearly in $\mathcal{NP}$ and we don't know how to solve it in polynomial time.

Many cryptographic protocols are based on the difficulty of factoring large composition integers. Factorisation, the basis of RSA, is believed to be neither $\mathcal{P}$ or $\mathcal{NP}$-complete.


### $\mathcal{NP}$-hard
A problem is $\mathcal{NP}$-hard if all $\mathcal{NP}$ problems can be polynomially reduced to it.

So the difference between $\mathcal{NP}$-complete and $\mathcal{NP}$-hard is that an $\mathcal{NP}$-complete problem must be in $\mathcal{NP}$.

An $\mathcal{NP}$-hard problem:
- does not need to be in $\mathcal{NP}$
- does not need to be a decision problem

For example, the TSP is $\mathcal{NP}$-hard; the decision version of the TSP is $\mathcal{NP}$-complete.