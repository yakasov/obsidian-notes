![[Pasted image 20231010090406.png]]

## Regular Expression $\implies$ Finite Automata
Given a regular expression, we can construct a finite automaton (NFA or potentially DFA) which recognises it language.

0. start the algorithm with a draft of a machine that has:
   - a start state
   - a single final state
   - an edge labelled with the given regular expression as follows:![[Pasted image 20231010090939.png]]
1. if an edge is labelled with $\emptyset$, then erase the edge.
2. transform any edge of the form from $a$ to $b$:![[Pasted image 20231010091250.png]]
3. transform any edge of the form from $a$ to $b$:![[Pasted image 20231010091303.png]]
Continue these operations until no labels can be broken up any further.

Example: Construct an NFA for the regular expression $a^\ast + ab$.
0. ![[Pasted image 20231010091415.png]]
2. ![[Pasted image 20231010091445.png]]
4. <br> ![[Pasted image 20231010091503.png]]
3. <br> ![[Pasted image 20231010091522.png]]


## Finite Automaton $\implies$ Regular Expression
To obtain the opposite direction (informally), we eliminate states and compose the transitions into more complex expressions until just a start and final state are connected by the final regular expression.

1. create a new start state $s$ and draw a new edge labeled with $\Lambda$ from $s$ to the original start state
2. create a new final state $f$ and draw new edges labeled with $\Lambda$ from all the original final states to $f$
eg the initial DFA
![[Pasted image 20231010091857.png]]
becomes 
![[Pasted image 20231010091908.png]]
3. merge edges: for each pair of states $i$ and $j$ with more than one edge from $i$ to $j$, replace all the edges from $i$ to $j$ by a **single edge** labeled with the regular expression formed by the *sum of the labels* on each of the edges from $i$ to $j$.
eg
![[Pasted image 20231010092019.png]]
4. eliminate states: step by step eliminate states (one at a time) and change the corresponding labels until the only states remaining are $s$ and $f$

When we delete a state, we must replace any possible transitions that went through it with a regular expression which carries the information that was removed.

**Before elimination of state $k$:**
![[Pasted image 20231010092215.png]]
$old(i, j)$ denotes the label on the edge between $i$ and $j$ before elimination; analogously for $old(k, j), old(i, k)$ and $old(k, k)$

If no edge exists, label it $\emptyset$, e.g for a loop.

**After elimination:**
![[Pasted image 20231010092324.png]]
The label: $new(i, j) = old(i, j) + old(i, k)old(k, k)^{\ast}old(k, j)$

The labels of all other edges, not involving state $k$, remain the same.

Step 4 (the elimination step) is repeated and step by step all states except $s$ and $f$ are eliminated. We end up with a two-state machine with a single edge between $s$ and $f$ labeled with the desired regular expression: $new(s, f)$.

Example: initial DFA
![[Pasted image 20231010092631.png]]

Steps 1 and 2 add start and final states:
![[Pasted image 20231010092650.png]]

Apply step 3 (sum):
![[Pasted image 20231010092720.png]]

Eliminate state 2: no changes to other edges (there are no paths passing through state 2)
![[Pasted image 20231010092742.png]]

Eliminate state 0:
![[Pasted image 20231010092803.png]]

Eliminate state 1:
![[Pasted image 20231010092814.png]]

Final regular expression: $a(a + b)^\ast$


## Finding minimum state DFA
In some cases our constructions can lead to complicated DFAs having more states than are really necessary. We can simplify the resulting DFA, however!

> [!info] Theorem (Myhill-Nerode Theorem)
> Every regular expression has a unique (up to a single renaming of the states) minimum state DFA.

To find a DFA with the minimum number of states:
1. find all pairs of equivalent (indistinguishable) states
2. combine equivalent states into a single state, modifying the transitions functions appropriately

### Equivalent states
First, we define two states $s$ and $t$ to be equivalent if for all possible strings $w$ left to consume (including $\Lambda$), DFA after "consuming" $w$ will finish in the same type of state (final/non-final).

That is, once you arrive in $s$ or $t$, equivalent states always lead to the same result "reject/accept" for any given string.

Two states are not equivalent if $\exists$ a string $w$ such that "following" $w$ from $s$ to $t$ will finish
- in the final state for one state and
- in the non-final state for the second state

Example:
![[Pasted image 20231010093658.png]]

States 0 and 1 are not equivalent e.g with the input $a$
States 1 and 2 are equivalent - starting in either, $b^\ast$ is rejected and anything with $a$ in it is accepted.

*see also lecture A/5 slides 26-29 for grid of pairs of states*

#### How to find the equivalent states
Begin with clearly distinguishable pairs (final and non-final):

$E_0 = \{\{s, t\} \:|\: s$ and $t$ are distinct and either both states are final or both states are non-final$\}$
e.g. $E_0 = \{\{1, 2\}, \{0, 1\}, \{0, 3\}, ...\}$, but $\{3, 4\} \notin E_0$  

Next, eliminate all pairs, which on the same input symbol, lead to a distinguishable pair of states, construct $E_1$.

$E_1 = \{\{s, t\} \:|\: \{s, t\} \in E_0$ and for every $x \in \Sigma$ either $T(s, x) = T(t, x)$ or $\{T(s, x), T(t, x)\} \in E_0\}$ 
e.g From the set $E_0$ we can eliminate $\{0, 1\}$ because
- $T(1, a) = 4$
- $T(0, a) = 3$
- $\{3, 4\} \notin E_0$ 

Repeat this process until there are some changes - calculate the sequence of sets of pairs $E_0 \supseteq E_1 \supseteq E_2 \supseteq ...$ as follows:

$E_{i + 1} = \{\{s, t\} \:|\: \{s, t\} \in E_1$ and for every $x \in \Sigma$ either $T(s, x) = T(t, x)$ or $\{T(s, x), T(t, x)\} \in E_i\}$  

Stop when $E_{k + 1} = E_k$ for some $k$, the remaining pairs are indistinguishable.

## Summary (general process)
1. start with a regular expression $\text{exp}_0$  
2. construct an NFA that recognises the given expression $\text{exp}_0$
3. transform the constructed NFA to the equivalent DFA
4. simplify the DFA to the one with the minimum number of states
5. find out the regular expression $\text{exp}_1$ which is recognised by the minimal DFA

$\text{exp}_0$ and $\text{exp}_1$ are equivalent, meaning they generate the same language.