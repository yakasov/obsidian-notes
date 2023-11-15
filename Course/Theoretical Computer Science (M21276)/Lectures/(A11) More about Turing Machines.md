##### TMs that don't halt
It is possible for a TM to not help, as shown here:
![[Pasted image 20231108131423.png]]
Let $L$ be the language accepted (recognised) by a TM:
- if the input string is in the language $L$, then *the machine must halt* (in a finite number of steps)
- for a string that is not in the language $L$, the TM can finish in a non-halt state or *get stuck in a loop/go on forever*

It is important to realise the difference:
	*to finish in a non-halt state or not halt at all.*

### Recursive and recursive enumerable languages
> [!info]  Definition
> A language $L$ is *recursive (decidable)* if $L$ is the set of strings accepted by some TM that halts on *every* input.
> A language $L$ is *recursively enumerable* if $L$ is the set of strings accepted by some TM.

If $L$ is a recursive enumerable language then:
- if $w \in L$ then a TM halts in a final state
- if $w \notin L$ then a TM halts in a non-final state or loops forever

If $L$ is a recursive language then:
- if $w \in L$ then a TM halts in a final state
- if $w \notin L$ then a TM halts in a non-final state

Every recursive language is also recursively enumerable - but not the opposite. There are many languages that are not even recursively enumerable (hence no grammar exists to describe their structure).

> [!faq] Hilbert's Polynomial Problem
> **Find an algorithm to determine whether a given polynomial with integer coefficients has an integer root (for example $6x^3yz^3 + 3xy^2 - x^3 - 10$).**
> 
> Let $D = \{p \: | \: p$ is a polynomial with an integer root$\}$
> Is the set $D$ recursive (decidable)?
> 
> A set is recursive (computable/decidable) if there is an algorithm which terminates after a finite amount of time and correctly decides whether or not a given element belongs to a set.
> 
> Is there a TM that halts on every input and answers YES or NO correctly?