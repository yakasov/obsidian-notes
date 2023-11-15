Turing machines can do more than finite automata and pushdown automata - they can read an input, perform transformations of the string on the tape and write down a result on the tape. These machines, which operate on an input to produce an output, are sometimes called transducers.

For example, a Turing machine can do mathematical operations like sums, products and much more.

##### Computing functions with Turing machines
With an input string $x$, we can say that the Turing machine can output string $y$ and then halt. From this, we can define a *partial* function $T(x) = y$ for all strings $x$ for which TM halts. This means that the Tm can compute the values of functions on strings.

We represent non-negative integers in other ways, e.g. $n$ by a string $n + 1$ (or $n$), or in binary format.

> [!faq] Example: Simple Turing machine for adding 2
> **Input:** a natural number $n$
> **Output:** $n + 2$
> 
> We can represent natural numbers in unary form (e.g. $3 = 111, 5 = 11111$) and $0$ will be represented by the empty symbol $\square$.
> 
> We only need 3 states: 0 (initial), 1 and Halt; as well as three instructions:
> 1. $(0, 1, 1, L, 0)$ - move left to blank cell
> 2. $(0, \square, 1, L, 1)$ - write 1 into cell and move left
> 3. $(1, \square, 1, S, Halt)$ - write 1 into cell and halt
> 
> Graphically:
> ![[Pasted image 20231107133029.png]]
> 
> In tape (instantaneous description):
> 	<p  class="tab"/>State 0: $\square \: _!1_! \: 1 \: 1 \: \square$
> State 0: $_!\square_! \: 1 \: 1 \: 1 \: \square$
> State 1: $_!\square_! \: 1 \: 1 \: 1 \: 1 \square$
> Halt: $\square \: _!1_! \: 1 \: 1 \: 1 \: 1 \square$

### Non-deterministic Turing machines
Non-determinism like in PDA (partially NFA): for one input configuration there are several possible outputs. The non-deterministic TM is like a normal TM but with a finite number of choices of moves - it may have more than 1 move with the same input "current state and symbol".

The non-deterministic TM accepts the input $w$ if there is at least one computation that halts normally for the input $w$.
![[Pasted image 20231107140158.png]]
> [!info] Theorem
> If a nondeterministic Turing machine accepts a language $L$, then there is a deterministic Turing machine that also accepts $L$.

Both deterministic and non-deterministic Turing machines accept the same family of languages (recursive enumerable), those of the unrestricted grammar.

### Turing machine variations
##### Two stack pushdown automaton
![[Pasted image 20231107140439.png]]
The right half of the tape is kept on one stack, and the left half on the other. As we move along, we pop characters off one and push them onto the other.

##### Semi-infinite tape Turing machine
![[Pasted image 20231107140510.png]]
Tape is infinite in only one direction. We can emulate a standard Turing machine by splitting the cells into two groups (every other one):
- one group represents the left half of infinite tape
- the other represents the right half

##### Multi-track Turing machine
![[Pasted image 20231107140556.png]]
Tape head reads/writes $k$-tracks at the same time. A multi-track TM can simulate a standard TM (ignore all but first track). A standard TM (with ${\Sigma}'$) can simulate a multi-track TM (with $\Sigma$) if we map every order pair $[x_1, x_2, ..., x_k]$ of symbols from $\Sigma$ to a unique symbol in ${\Sigma}'$, where $|{\Sigma}'| = |{\Sigma}|^k$.

##### Multi-tape Turing machine
![[Pasted image 20231107140842.png]]
$k$-tapes with $k$-tape heads moving independently (generalisation of multi-track Turing machine) - each TM has its own read-write head, but the state is common for all.

In each step (transition), TM reads symbols scanned by all heads, depending on those and current state, each head writes, moves R or L, and control-unit enters into a new state. The actions of heads are independent of each other.

> [!faq] Example: multiplying two numbers to get a third
> This would be fairly difficult to do with a simple Turing machine, but is trivial with a three tape machine.
> ![[Pasted image 20231107141030.png]]
> 
> Start by checking to see whether either number is zero:
> $(0, (\square, \square, \square), (\square, \square, \square), (S, S, S), \text{Halt})$ - both are zero
> $(0, (\square, 1, \square), (\square, 1, \square), (S, S, S), \text{Halt})$ - first is zero
> $(0, (1, \square, \square), (1, \square, \square), (S, S, S), \text{Halt})$ - second is zero
> $(0, (1, 1, \square), (1, 1, \square), (S, S, S), 1)$ - both are non-zero
> 
> Add the number on the second tape to the third tape:
> $(1, (1, 1, \square), (1, 1, 1), (S, R, R), 1)$ - copy
> $(1, (1, \square, \square), (1, \square, \square), (S, L, S), 2)$ - done copying
> 
> Move the tape head of the second tape back to the left end of the number, then move the tape head of the first number one cell to the right:
> $(2, (1, 1, \square), (1, 1, \square), (S, L, S), 2)$ - move to the left end
> $(2, (1, \square, \square), (1, \square, \square), (R, R, S), 3)$ - both types to the right one cell
> 
> Check the first tape head to see if all additions have been performed:
> $(3, (\square, 1, \square), (\square, 1, \square), (S, S, L), \text{Halt})$ - done
> $(3, (1, 1, \square), (1, 1, \square), (S, S, S), 1)$ - do another add

![[Pasted image 20231107141829.png]]
**Every multi-tape TM has an equivalent single tape TM.**
- if $M$ has $k$ tapes, $M'$ simulates the effect of $k$ tapes by storing the same information on its single tape
- it uses a new symbol # as a delimiter to separate the contents of the different tapes (marks the left or right end of the relevant portions of the tape)
- $M'$ must also keep track of the locations of the heads on each tape
	- writes a tape symbol with a dot above it to mark where the head on that tape would be
	- dotted symbols are simply new symbols added to the tape alphabet
- if the movement of one $T$'s tape heads causes $M'$'s tape head to bump into either or #, then that side of type must be moved to make room for a new type cell.

##### Multi-head Turing machine
![[Pasted image 20231107142159.png]]
One tape with many tape heads moving independently. Only one head can be active at any given time, with a particular head being associated with each stated 

##### Off-line Turing machine
A two tape TM where one tape is a read-only version of the input.

##### Multi-dimensional tape
Where the tape may extend into two or more dimensions.


### Linear Bounded Automata
If we restrict the amount of tape for TMs, then the machines become less powerful.

A *linear bounded automaton* (LBA) is a Turing machine which can only use a tape the size of the initial input, i.e. it cannot use any more tape than the size of the initial input.

LBAs recognise exactly the family of context-sensitive languages.

