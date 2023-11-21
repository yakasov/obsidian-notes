## Non-deterministic Pushdown Automata
NPDAs are like finite automata, except they also have a stack memory where they can store an arbitrary amount of information.
![[Pasted image 20231015135735.png]]
Read/write stack memory works as LIFO: Last In, First Out

Stack operations:
- the *pop* operation reads the top symbol and removes it from the stack
- the *push* operations writes a designed symbol onto the top of the stack, e.g. push($X$) means put $X$ on top of the stack
- the *nop* operation does nothing to the stack 
The stack symbols are different to the "language" alphabet used on the input tape.

We start with:
- only the initial stack symbol on the stack (and nothing else)
- in the start state of the control automaton

### Transitions (informally)
At each step, the state, input element and top symbol in the stack determine the next step (transition).

One transition step includes:
- change the state (as FA)
- (possible) reading of a symbol from the input tape and moving to the next right symbol (as FA)
- change the stack (pushing a symbol onto the stack / popping a symbol of the stack / no changes to the stack)
Transition steps are formally defined by transition functions (often in the form of the transition instructions).

Three inputs:
- state $p$
- input character $a$ (also $\lambda$)
- stack character $A$ 

Two outputs:
- "new" state
- stack operation

What do we do to the stack?
*pop, push($B$)*, ($B$ is one of the stack characters), or *nop*

If $a \neq \lambda$, the head is automatically moved to the next symbol.

### Describing NPDAs
NPDAs can be described by:
- a finite set $Q$ of states (and the start state and the set of accepting / final states)
- a finite set $\Sigma$ which is called the input alphabet
- a finite set $Y$ which is called the stack alphabet (and the initial stack symbol $\$$)
- a finite set of transition instructions (or a transition function $T$)
	$$T : Q \times \Sigma \cup \{\lambda\} \times \Gamma \rightarrow \Gamma^\ast \times Q\}$$
	(or represented by a "transition" diagram)

> [!faq] Example:
![[Pasted image 20231015140900.png]]
We can rewrite the transition using the transition function:
>$$T(p, a, A) = (push(B), q)$$
>
> or more often as the transition instruction
>$$(p, a, A, push(B), q)$$

### When is a string accepted/rejected by NPDA?

>[!info] Definition
> A string is *accepted* by an NPDA if there is some path (i.e sequence of instructions) from the start state to a final state that consumes all the letters of the string.
> Otherwise, the string is *rejected* by the NPDA.

**The language of an NPDA is the set of all strings that it accepts.**

When is an input string rejected by the NPDA?
- if reading an input string finishes without reaching a final state
- if, for a current state/symbol on the stack/input symbol, there is no transition
- if it attempts to pop the empty stack

> [!faq] Example:
**Build an NPDA which recognises the context-free language:
> 	$L = \{a^nb^n \:|\: n \geq 0\}$** 
> 	
> 	Plan:
> 1. begin reading the string, and for each $a$ read, push a $Y$ onto the stack
>2. on the first $b$ change states, and begin removing one $Y$ from the stack for each $b$
>3. if you reach the end of the input and have just cleared the stack, accept the string
>4. otherwise reject (e.g if the stack runs out before the input - more $b$'s than $a$'s)
>
> **In terms of an NPDA:**
> Three states: 0 (start), 1, 2 (final)
> Input alphabet: $\{a, b\}$
> Stack alphabet $\{Y, \$\}$
> ![[Pasted image 20231015141801.png]]
> 
> There are 6 allowed instructions for this NPDA:
> $T_x:$ (state, character, stack, function, next state)
> $T_1: (0, a, \$, push(Y), 0)$
> $T_2: (0, a, Y, push(Y), 0)$
> $T_3: (0, \lambda, \$, nop, 2)$
> $T_4: (0, b, Y, pop, 1)$
> $T_5: (1, b, Y, pop, 1)$
> $T_6: (1, \lambda, \$, nop, 2)$
> 
> Reading $\$$ corresponds to check if the stack is empty.

### Representing a computation
As the NPDA reads in the input, it changes states and modifies the stack. To describe the process at any instant, we need to keep track of three things:
- the current state
- what input characters are left
- what is on the stack
The best way of doing this is to use *the instantaneous description:*
	*(current state, unconsumed input, stack contents)*

#### Sample transition
$Z$ is the in-between in the stack that we don't really care about.
Suppose an NPDA has the instantaneous description:
$$(0, abba, {Y}Z\$)$$
and the NPDA includes an instruction of the following form:
$$(0, a, Y, pop, 1)$$
After a transition the description is changed to:
$$(1, bba, Z\$)$$	![[Pasted image 20231016163527.png]]

Further examples:
	Start $\rightarrow (0, aabb, \$)$
	$T_1 \rightarrow (0, abb, {Y}\$)$
	$T_2 \rightarrow (0, bb, {Y}{Y}\$)$
	$T_4 \rightarrow (1, b, {Y}\$)$
	$T_5 \rightarrow (1, \lambda, \$)$
	$T_6 \rightarrow (2, \lambda, \$)$
Final state, nothing left on the input, so accept the string.

### NPDAs and context-free languages
Let's consider:
- the class of context-free languages generated by context-free grammars
$$N \rightarrow \alpha$$
   where $N$ is a non-terminal and $\alpha$ is any string over the alphabet of terminals and non-terminals
- the class of languages accepted by all NPDAs

> [!info] Theorem
> The context free-languages are exactly the languages that are accepted by non-deterministic pushdown automata!

The theorem can be proved by construction in two steps:
1. take an NPDA $\rightarrow$ a context-free grammar that can be found which generates a language accepted by the given NPDA
2. take a context-free language $\rightarrow$ an NPDA can be found that accepts the given context-free language

> [!faq] Example
> **Show that the language containing all strings over $a, b$ with exactly the same number $a$'s and $b$'s is context-free**
> 
> Plan:
> - keep track of the difference between the number of $a$'s and $b$'s we've read by changing the symbols in the stack
> - use one symbol $X$ if we've seen more $a$'s and another $Y$ if we've seen more $b$'s
> 
> ![[Pasted image 20231016170408.png]]
> Two states: 0 (start), 1 (final)
> Input alphabet: $\{a, b\}$
> Stack alphabet: $\{X, Y, \$\}$
> 
> **Instructions:**
> $T_1: (0, a, \$, push(X), 0)$
> $T_2: (0, a, X, push(X), 0)$
> $T_3: (0, a, Y, pop, 0)$
> $T_4: (0, b, \$, push(Y), 0)$
> $T_5: (0, b, Y, push(Y), 0)$
> $T_6: (0, b, X, pop, 0)$
> $T_7: (0, \lambda, \$, nop, 1)$
> 
> **Step by step for $abbbaa$:**
> Start $\rightarrow (0, abbbaa, \$)$
> $T_1 \rightarrow (0, bbbaa, X\$)$
> $T_6 \rightarrow (0, bbaa, \$)$
> $T_4 \rightarrow (0, baa, Y\$)$
> $T_5 \rightarrow (0, aa, YY\$)$
> $T_5 \rightarrow (0, a, Y\$)$
> $T_5 \rightarrow (0, \lambda, \$)$
> $T_6 \rightarrow (1, \lambda, \$)$

### Determinism vs non-determinism
Like finite automata, push-down automata can be either deterministic or non-deterministic.

A deterministic PDA *never has a choice of the next step!* It has *at most one* possible output for every combination of state, input character and stack character (compared to DFA).

Be careful: for every combination of state and stack character only of the transactions is allowed: either for the empty symbol $\lambda$ or for an input symbol (or there can be no transaction at all).

> [!faq] Example
> A non-deterministic push-down automaton can contain the following instructions, but a deterministic one can't.
> 
> Ex1: $(0, a, \$, push(Y), 0); (0, a, \$, pop, 1)$
> Ex2: $(0, \lambda, \$, pop, 3); (0, b, \$, nop, 2)$

Recall that for finite automata, DFAs and NFAs accepted the same languages - regular ones.

Deterministic PDAs cannot recognise the whole family of context-free languages, however.

> [!faq] Example - palindrome NPDA
> **Design a push-down automaton which recognises even length palindromes:
> $L = \{ww^R \:|\: w \in \{a, b\}^+\}$**
> 
> Plan:
> - read in a string and save it to the stack
> - at each step, consider the possibility you might have reached the middle
> - once reaching the midpoint, start working backwards, removing things from the stack if they match what was saved
> 
> ![[Pasted image 20231016172638.png]]
> **Step by step for $aabbaa$:**
> Start $\rightarrow (0, aabbaa, \$)$
> Load stack $\rightarrow (0, abbaa, X\$)$
> Load stack  $\rightarrow (0, bbaa, XX\$)$
> Load stack $\rightarrow (0, baa, YXX\$)$
> Try, is this the middle? $\rightarrow (1, baa, YXX\$)$
> Pop stack $\rightarrow (1, aa, XX\$)$
> Pop stack $\rightarrow (1, a, X\$)$
> Pop stack $\rightarrow (1, \lambda, \$)$
> Done! $\rightarrow (2, \lambda, \$)$

#### DPDAs versus NPDAs
This was an example of a non-deterministic PDA, because from state 0 it branches, either loading another letter on or trying to take letters off.

This could only be done non-deterministically! A deterministic PDA would need to know when to start removing letters from the stack. Thus an NPDA can recognise the language of the even palindromes, but a DPDA cannot.

*Deterministic PDAs recognise regular languages and also some which are not regular, but not all of the context-free languages.*
![[Pasted image 20231016173236.png]]
