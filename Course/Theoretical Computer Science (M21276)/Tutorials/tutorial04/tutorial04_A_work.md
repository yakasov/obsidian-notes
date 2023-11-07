**Question 1**
We are given the following DFA over the alphabet $\{a, b\}$:
![[Pasted image 20231005104553.png]]
i. Which of the strings $aaa$ and $aba$ are accepted by the DFA?
  $aaa$ is accepted as we can go $0 \rightarrow 1 \rightarrow 3 \rightarrow 2$ to spell $aaa$.
  $aba$ is not accepted as we cannot add a single $a$ after spelling $ab$ (from state 2). <span class="tick">✓</span>
ii. Three strings of length at least 5 which are accepted:
  $bbbaa, abbab, aaaaa$ <span class="tick">✓</span>
iii. Three strings of length at least 5 which are NOT accepted:
  $ababa, bbbaba, aabaa$ <span class="tick">✓</span>
iv. The transition function $T$ for the DFA:
  $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b\}$
  $T(0, a) = 1$
  $T(0, b) = 0$
  $T(1, a) = 3$
  $T(1,b) = 2$
  $T(2,a) = 1$
  $T(2, b) = 3$
  $T(3,a) = 2$
  $T(3, b) = 3$ <span class="tick">✓</span>
  <span class="cross">. T(0, b) = 0<br>T(1, a) = T(2, b) = T(3, b) = 3 etc<br>combine transitions that result in the same state</span>

**Question 2**
We are given the following NFA over the alphabet $\{a, b\}$:
![[Pasted image 20231005105633.png]]
i. Which of the strings $aaa, ba$ and $ab$ are accepted by the NFA?
  $aaa$ is accepted as we can go $0 \rightarrow 0 \rightarrow 2 \rightarrow 3$ to spell $aaa$. <span class="tick">✓</span>
  $ba$ is accepted as we can go $0 \rightarrow 1 \rightarrow 2 \rightarrow 3$ to spell $ba$. <span class="tick">✓</span>
  $ab$ is not accepted as we cannot end a string in $b$. <span class="tick">✓</span>
ii. A string of length at least 5 which is accepted:
  $aaaaa$ <span class="tick">✓</span>
iii. A string of length 5 which is not accepted:
  $aaaab$ <span class="tick">✓</span>
iv. The transition function $T$ for the given NFA:
  $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b\}$
  $T(0, a) = 0 \:|\: 2$ <span class="tick">✓</span> <span class="cross">{0, 2}</span>
  $T(0, \Lambda) = 1$ <span class="tick">✓</span>
  $T(1, b) = 1 \:|\: 2$ <span class="tick">✓</span> <span class="cross">{1, 2}</span>
  $T(2, a) = 3$ <span class="tick">✓</span> 
  $T(3, \Lambda) = 2$ <span class="tick">✓</span>

**Question 3**
i. $a + b$ over the alphabet $\Sigma = \{a,b\}$
  results in $\{a, b\}$
  
  set $Q$ of states: $\{0, 1\}$
  start state: 0
  end state: 1
  
   $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b\}$
   $T(0, a) = T(0, b) = 1$ <span class="tick">✓</span>
ii. $a + b^\ast$ over the alphabet $\Sigma = \{a, b\}$
  results in $\{a, b, bb, bbb, bbbb, ...\}$
  
  set $Q$ of states: $\{0, 1, 2\}$
  start state: 0
  end states: 1, 2
  
   $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b\}$
   $T(0, a) = 1$
   $T(0, b) = 2$ 
   $T(1, b) = 2$ <span class="tick">✓</span>
iii. $ab^\ast + bc^\ast$ over the alphabet $\Sigma = \{a, b, c\}$
  results in $\{ab, abb, abbb, abbb, ... bc, bcc, bccc, bcccc, ...\}$
  
  set $Q$ of states: $\{0, 1, 2, 3\}$
  start state: 0
  end state: 3
  
   $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b, c\}$
   $T(0, a) = 1$
   $T(0, b) = 2$
   $T(1, b) = 1 \:|\: 3$
   $T(2, c) = 2 \:|\: 3$ <span class="tick">✓</span>
<span class="cross">Include an additional state - 'all other transitions go to state x'</span>

**Question 4**
i. $a^{\ast}bc^\ast + ac$ over the alphabet $\Sigma = \{\Lambda, a, b, c\}$
  results in $\{a^nbc^m \:|\: ac, n \geq 0, m \geq 0\}$
  
  set $Q$ of states: $\{0, 1, 2, 3, 4\}$
  start state: 0
  end state: 2, 4
  
   $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{\Lambda, a, b, c\}$
   $T(0, a) = 1$
   $T(0, \Lambda) = 3$
   $T(1, c) = 2$ 
   $T(3, a) = 3$
   $T(3, b) = 4$
   $T(4, c) = 4$ 
ii. $(a + b)^{\ast}a$ over the alphabet $\Sigma = \{a, b\}$
  results in $\{a, aa, aaa, aaaa, ..., ba, bba, bbba, ...\}$
  
  set $Q$ of states: $\{0, 1\}$
  start state: 0
  end state: 1
  
  $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{a, b\}$
  $T(0, b) = 0$
  $T(0, a) = 1$
  $T(1, a) = 1$
iii. $a^\ast + ab$ over the alphabet $\Sigma = \{\Lambda, a, b\}$
  results in $\{\Lambda, ab, a, aa, aaa, aaaa, ...\}$
  
  set $Q$ of states: $\{0, 1, 2, 3\}$
  start state: 0
  end state: 3
  
  $T : Q \times \Sigma \rightarrow Q$, where $\Sigma = \{\Lambda, a, b\}$
  $T(0, a) = 1$
  $T(0, \Lambda) = 2$
  $T(1, b) = 3$
  $T(2, a) = 2$
  $T(2, \Lambda) = 3$
<span class="cross">'all other transitions are equal to null set'</span>

**Question 6**
Convert the following NFA to an equivalent DFA over the alphabet $\{a, b\}$:
![[Pasted image 20231005161017.png]]
  By changing the transition
    $T(1, \Lambda) = 2$ 
  to
    $T(1, b) = 0$
  we can remove the need for the $\Lambda$ transition to state 2 entirely.
<span class="cross">Answer:</span>
![[Pasted image 20231009165644.png]]
