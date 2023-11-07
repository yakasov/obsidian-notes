#### Models of Computing
Each level of language in the Chomsky hierarchy (Regular languages -> Context-free languages -> Context sensitive grammar -> Unrestricted grammar) has a computing model associated with it.

##### Differences between models
- Compare pushdown automata and finite automata:
	- both have finite state control
	- both can only *read* a string
	- the reading head can only *move to the right* (reading a symbol) or *stay at the same position*
	- stack - temporary infinite storage - creates the difference between them
- Pushdown automata are more powerful than finite automata (there are context-free languages that are not regular, e.g. $\{a^nb^n, n \geq 0\}$)
- However, pushdown automata are limited in scope (e.g. $\{a^nb^nc^n, n \geq 0$} is not a context-free language)

If there is no storage $\implies$ finite automata
If the storage is a stack $\implies$ pushdown automata
If the storage consists of 2 or 3 stacks $\implies$ ???

#### Turing Machines
Turing machines are more powerful than both finite automata or pushdown automata - they are as powerful as any computer we have ever built.

They offer infinite "all" accessible memory (in the form of a tape) and the option to read and write to it. They also have a read/write head that can move left and right on the input tape.

##### Basic properties of a Turing machine
![[Pasted image 20231106133237.png]]
The Turing machine (TM) works on an infinite tape divide into cells (infinite in both directions), each of which contains either a symbol from an alphabet or the blank symbol (only a finite number of non-blank symbols is written on the tape).

The TM is always in one of a finite number of states. The read/write head reads the symbol in the "current cell" and depending on the symbol and the current state:
- can change the state
- can move the head in either direction or not move at all
- re-write the "current symbol" or leave it unchanged

At each step there are three possible movements for the head:
- move to the left by one cell ($L$)
- stay at the current cell ($S$)
- move to the right by one cell ($R$)

##### TM instructions (transition functions)
Each Turing machine instruction contains the following five parts:
- **IN:** The *current machine state* (from $Q$)
- **IN:** The tape symbol *read* from the current tape cell (may be a blank symbol) (from $\Gamma$)
- **OUT:** A tape symbol to *write* into the current tape cell (may be a blank symbol or any other symbol) (from $\Gamma$)
- **OUT:** The *next* machine state (from $Q$)
- **OUT:** A *direction* for the tape head to move in $\{L, R, S\}$
	$T : Q \times \Gamma \rightarrow \Gamma \times Q \times \{L, R, S\}$  
Two inputs, three outputs: $T(i, a) = (b, j, R)$
$\Gamma$ contains $\Sigma$ (the alphabet of the language) and the "empty tape symbol" - $\square$, but also other symbols

###### Instruction shorthand
A full Turing machine instruction can be represented as instructions:
	$(i, a, b, L ,j)$ 

If the *current state* of the machine is $i$, and if the symbol in the current tape cell is $a$, then *write* $b$ into the current tape cell, *move left* ($L$) by one cell, and go to state $j$.
![[Pasted image 20231106134718.png]]

An input string is represented on the tape by placing the letters of the string (from $\Sigma$) into adjacent tape cells. All other cells of the tape contain the blank symbol $\square$. The head is usually positioned over the *leftmost* cell of the input string (the leftmost non-blank tape symbol).

As is the case for FAs or PDAs, there is one start state which must be specified. However, in the case of a TM, there is usually one final state (also called "Halt").

A Turing machine *stops (halts)* when it either:
- enters the Halt state or
- when it enters a state for which there is no valid move

##### Using Turing machines to recognise languages
A Turing machine $T$ recognises a string $x$ (over $\Sigma$) if and only when
- $T$ starts in the initial position and $x$ is written on the tape
- $T$ halts in a final state

$T$ is said to recognise a language $A$ if $x$ is recognised by $T$ if and only if $x$ belongs to $A.$ Be aware that while running a TM can also read/write other symbols from/onto a tape, not necessarily only those from the alphabet $A$.

A Turing machine $T$ does not recognise a string $x$ if $T$ does not halt or halts in a state that is not final.

To describe the TM at any given time we need to know three things:
1. What is on the tape?
2. Where is the tape head?
3. What state is the control in?

We'll represent this information as follows:
	State $i : \square \: a \:  a \: _ib_i \: a \: b \: \square$ 
Here, the $\square$ symbol represents an empty cell (repeated indefinitely left and right) and the position of the tape head is marked.

> [!faq] Example: TM for $a^{\ast}$
> **For $\Sigma = \{a, b\}$ design a Turing machine that accepts the language denoted by the regular expression $a^\ast$.**
> 
> - Starting at the left end of the input, we read each symbol and check that it is $a$.
> - If it is, we continue moving right.
> - If we reach a blank symbol without encountering anything but $a$, we terminate and accept the string.
> - If the input contains a $b$ anywhere (the string is not in $L(a^{\ast}$)) we halt in a non-final state.
>
> To keep track of the computation, two states $0$ (initial) and $1$ (final) are sufficient. As the transition function we can use:
> 	$T(0, a) = (0, a, R)$
> 	$T(0, \square) = (1, \square, R)$
> Or we can draw a figure:
> ![[Pasted image 20231106141945.png]]




