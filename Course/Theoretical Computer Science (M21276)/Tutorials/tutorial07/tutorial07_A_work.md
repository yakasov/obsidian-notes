A context-free grammar is a grammar with productions
	$A \rightarrow \alpha$
$A \in N$ and $\alpha \in (N \cup T)^\ast$. A language is context-free if it is generated by a context-free grammar.

Producing context-free grammars for the following languages:

1. $L = \{ab^ncd^n \:|\: n \geq 0\}$ over the alphabet $\Sigma = \{a, b, c, d\}$.
   Four states: 0 (start), 1, 2, 3 (final)
   Stack alphabet: $\{X, \$\}$
   $T_1 : (0, a, \$, \text{nop}, 1)$
   $T_2: (1, b, \$, \text{push}(X), 1)$
   $T_3: (1, b, X, \text{push}(X), 1)$
   $T_4: (1, c, \ast, \text{nop}, 2)$
   $T_5: (2, d, X, \text{pop}(X), 2)$
   $T_6: (2, \Lambda, \$, \text{nop}, 3)$
   
   $S \rightarrow aA$
   $A \rightarrow bAd \:|\: c$
   Non-deterministic push-down automata

2. $L = \{wcw^R \:|\: w \in \{a, b\}^{\ast}\}$ over the alphabet $\Sigma = \{a, b, c\}$
   $\{a, b\}^{\ast} \times c \times \{a, b\}^R$ 