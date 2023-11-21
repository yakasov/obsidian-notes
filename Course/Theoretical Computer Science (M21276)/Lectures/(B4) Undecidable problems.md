### Halting problem
The Halting problem is undecidable, or more precisely, it is partially decidable.
We can prove this using a direct diagonalisation argument.

##### Acceptance formulation
Define the set 
$$\text{A} = \{<M, w>\ : M \:\text{is a TM that accepts}\: w\}$$
where $<M, w>$ is a unique coding.

So we consider all possible TMs (countable) and all possible strings (countable) and if $M$ accepts $w$, it belongs to $\text{A}$.

Another formulation of the halting problem - there is no TM that will recognise the set $\text{A}$! However, for some simpler computing models, such as finite automata or push-down automata, we can always find a TM which recognises $\text{A}$.

##### Proof
The proof is by contradiction.

> Suppose there were a machine $\text{SOLVER}$ that on every input $w$ and for every TM $\text{M}$ it would tell us if $\text{M}$ accepts or rejects $w$.

Build a new TM $\text{OPPOSER}$ that does the following:
- $\text{OPPOSER}$ takes the input $w$ and determines the TM $<w>$ that $w$ encodes (if the input is not the encoding of a TM, then $\text{OPPOSER} rejects the input)
- ask $\text{SOLVER}$ for the answer: *"Does the TM $<w>$ accept $w$?"*
- if $\text{SOLVER}$ accepts, then $\text{OPPOSER}$ rejects, and vice versa
$\text{OPPOSER}$ is a perfectly valid TM, because $\text{SOLVER}$ always halts.

But we run into problems if the input is the encoding of $\text{OPPOSER}$, if we let $<\text{OPPOSER}> = \tilde{w}$:
- $\text{OPPOSER}$ asks $\text{SOLVER}$ for an answer to *"Does the TM $<\tilde{w}>$ accept $\tilde{w}$?"*
- if $\text{SOLVER}$ claims that $\text{OPPOSER}$ accepts $\tilde{w}$, then $\text{OPPOSER}$ rejects $\tilde{w}$.
- if $\text{SOLVER}$ claims that $\text{OPPOSER}$ rejects $\tilde{w}$, then $\text{OPPOSER}$ accepts $\tilde{w}$.

Everything we did was fine except assuming that $\text{SOLVER}$ exists - so $\text{SOLVER}$ does not exist.


##### How do we prove a problem is undecidable?
- Contradiction - assume it is solvable and see if it leads to an internal contradiction, or conflicts with something else we believe is true
- Reduction - see if another unsolvable problem can be reduced to solving it. That is, if we assume it is solvable, then we can show that another problem we believe is unsolvable (like the halting problem) can be solved.

#### Post Correspondence Problem
An instance of the problem:

Given an alphabet $\Sigma$ and a finite sequence of pairs of strings over $\Sigma$:
$$(s_1, t_1), ..., (s_n, t_n)$$
Is there a sequence of indexes $i_1, ..., i_k$ with repetitions allowed, such that
$$ s_{i_1} ... s_{i_k} = t_{i_1} ... t_{i_k} ? $$

##### Tiling Problem
> [!info] Problem (Unbounded Tiling Problem) $\rightarrow$ Undecidable
> Is there an algorithm that can decide for a given particular set of tiles whether any sizes of floor $n \times n$ can be tiled?

> [!info] Problem (Bounded Tiling Problem) $\rightarrow$  Decidable
> Is there an algorithm that can decide for a given particular set of tiles whether a specific size of floor $n \times n$ can be tiled?

##### Hilbert's Tenth Problem
> [!info] Problem (Hilbert's Tenth Problem)
> Does a polynomial equation $p(x_1, ..., x_n) = 0$ with integer coefficients have a solution consisting of integers?

In 1970, Matiyasevich proved that the above problem is undecidable. This means there is no algorithm (TM) to decide whether an arbitrary polynomial equation with integer coefficients has a solution of integers.

But the problem is partially solvable, as we can write a TM which returns a solution, *if* it exists.
