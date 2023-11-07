**Models of computation**
Finite automata, push-down automata, Turing machines - all are abstract models of computers with different computational power:
- They all have an input tape, which contains a single string (input)
- The models can accept (or reject) the input strings (the set of all accepted strings over the alphabet is the language recognised by the model)
- They have different types of memory, e.g. finite or infinite, and some may have more additional features

**Finite automata**
A finite automaton (FA) has three component:
- an *input tape*, which contains an input string over $\Sigma$
- a *head* which reads the input string one symbol at a time
- *memory* - realised as a finite set $Q$ of states - the FA is always only in one state, called a *current state* of the automaton
The "program" of the FA defines how the symbols that are read change the current state.

**Graphical representations of FA**
We can represent finite automata as a *transition graph*:
![[Screenshot 2023-10-03 at 10.06.27.png]]
An input string over the alphabet $\Sigma = \{a, b\}$ is written on an input type, e.g. $abbbba$.

There is always one "initial" state and *at least* one "final" state (denoted by a double circle). There will often be more than one final state.

A finite automaton is always in a state (from the set of states $Q$):
- Begins in a designated initial (start) state
- On reading a symbol, the state changes - this is the transition
- New state depends on the current state and the symbol read in
- No option to re-read the input symbols or to write
At the end of the string, the machine either:
1. accepts the string if, and only if, its state is one of the final states, or
2. reject it otherwise.
*The language of the automaton is the set of strings it accepts.*

**Formal definition of FA**
![[Screenshot 2023-10-03 at 10.10.18.png]]
Set $Q$ of states: $\{0, 1, 2\}$
Start state: 0
Final state(s): 1

Transition functions:
$T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b\}$
- $T(0, a) = 1$
- $T(0, b) = 2$
- $T(1, a) = T(1, b) = 1$
- $T(2, a) = T(2, b) = 2$

**State transition function**
The *state transition function*, $T : Q \times \Sigma \rightarrow Q$, of the form
![[Pasted image 20231003101317.png]]
is represented by $T(i, a) = j$, where $i, j \in Q$ and $a \in \Sigma$.

To describe a full automaton formally we need to know:
- the finite set Q of states,
- which states are the start and final ones,
- the state transition function - "program"

**Deterministic finite automata (DFA)**
In the previous examples there was always exactly one option of transition for every state and every symbol - every node in the graph has exactly one edge coming out for each possible input symbol.

Such automata are called deterministic finite automata (DFA), where we know uniquely which state we are in following a particular string.

*A DFA over a finite alphabet $\Sigma$ is a finite directed graph with the property that each node emits one labeled edge for each distinct element of $\Sigma$.*
or, more formally,
*A DFA accepts a string $w$ over $\Sigma^\ast$ if there is a part from the start state to a final state such that $w$ is the concatenation of the labels on the edges of the path. Otherwise, the DFA rejects $w$.*

*The set of all strings over $\Sigma$ accepted by a DFA $M$ is called the language of $M$ and is denoted by $L(M)$.*

Example: construct a DFA to recognise the regular languages represented by the regular expression $(a + b)^\ast$ over the alphabet $\Sigma = \{a, b\}$.
	The language is the set of all possible strings over $\{a, b\}$. This can be recognised by
	![[Pasted image 20231003101920.png]]

Example: find a DFA to recognise the language represented by the regular expression $a(a + b)^\ast$ over the alphabet $\Sigma = \{a, b\}$.
	This is the set of all strings in $\Sigma^\ast$ which begins with $a$. One possible DFA is
	![[Pasted image 20231003102029.png]]

**Pattern matching**
Example (pattern recognition): build a DFA to recognise the regular language represented by the regular expression $(a + b)^{\ast}abb$ over the alphabet $\Sigma = \{a, b\}$.
	The language is the set of strings that begin with anything, but must end with the string $abb$.
	We're effectively looking for strings which have a particular pattern to them (similar to looking for all strings ending in ".doc" or ".pdf"). <br>
	The diagram below shows a DFA to recognise the language. We can use the states to keep track of what we have seen:
	![[Pasted image 20231003102347.png]] <br> We don't know when the string will end, so we keep track of the last three symbols we've seen:
	- If in state 1: the last character was $a$
	- If in state 2: the last two symbols were $ab$
	- If in state 3: the last three were $abb$

DFAs are very often used for pattern matching eg searching for words/structures in strings. An FA enables us to examine each symbol of a given input only once, allowing us to immediately discard symbols that do not match a given pattern.

*The class of regular languages is exactly the same as the class of languages accepted by DFAs* - this means for any regular language, we can find a DFA which recognises it (and vice versa). This is also the same for NFAs!

**Non-deterministic finite automata**
DFAs are called deterministic because following any input string, we know exactly which state it is in and path it took to get there. However, we can also have non-deterministic (NFA), where there may be more than one option we can follow with the same input character (or even no option at all).

An NFA recognises a string if *one of its possible states* which result are reading a whole string is a final state. Otherwise, it rejects it.

Informally, an NFA over an alphabet $\Sigma$ is a finite transition (directed) graph with each node having zero or more edges:
- each edge is labelled either with a letter from $\Sigma$ or with $\Lambda$
- multiple edges may go from the same node with the same label
- some letters may not have an edge associated with them. Strings following such paths are rejected

Example: draw an NFA to recognise the language of the regular expression $ab + a^{\ast}a$
	![[Pasted image 20231003103127.png]]
	- The upper path corresponds to $ab$ and the lower one to $a^{\ast}a$.
	- This is an NFA: it has a $\Lambda$ edge (allows us to travel to state 2 without consuming an input letter) and two $a$-edges from state 2.
	- If we see a $b$ from any state except state 1, the string is rejected.

If an edge is labelled with the empty string $\Lambda$, then we can move to the next state (along the edge) without consuming an input letter. Effectively we could be in either state, and so the possible paths could branch.

If there are two edges with the same label from one node, we can move along any of them.

Example: draw an NFA to recognise the language of the regular expression $ab + a^{\ast}a = ab + aa^\ast$.
	![[Pasted image 20231003103418.png]]
	This is also an NFA because from state 0 we can go in two directions if the input symbol is an $a$.

**NFA transition functions**
Due to non-determinism, the output of the transition function are sets of states, $T : Q \times \Sigma \rightarrow P(Q)$.

Example: if there are no edges from state $k$ labelled with $a$, we'll write
	$T(k, a) = \emptyset$
	If there are three edges from state $k$, all labelled with $a$, going to states $i, j$ and $k$, we'll write
	$T(k, a) = \{i, j, k\}$

All digital computers are deterministic; quantum computers are the first potential for non-deterministic machines. 

The usual mechanism for deterministic computers is to try one particular path and to backtrack if that path proves poor. Parallel computers make non-determinism almost realisable. For example, we can let each process make a random choice at each branch point, thereby exploring many possible trees.

**NFAs versus DFAs**
![[Pasted image 20231003104516.png]]
Since NFAs and DFAs recognise the same language, one is always able to find a DFA which recognises the language of a given NFA, demonstrating their equivalence. DFAs are a subset of NFAs, so we only need to show that we can map any NFA into a DFA.

**Finding of an equivalent DFA for a given NFA**
We can prove the equivalence of NFAs and DFAs by showing how, for any NFA, to construct a DFA which recognises the same language.

Generally the DFA will have more possible states than the NFA. If the NFA has $n$ states, then the DFA could have as many as $2^n$ states.

Example: if the NFA has three states $q_0, q_1, q_2$, then the DFA could have $2^3$ states:
	$\emptyset, \{q_0\}, \{q_1\}, \{q_2\}, \{q_0, q_1\}, \{q_1, q_2\}, \{q_0, q_1, q_2\}$
	
