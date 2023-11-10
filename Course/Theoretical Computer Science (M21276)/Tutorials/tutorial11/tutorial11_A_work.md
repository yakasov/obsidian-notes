1. $(0, \square, 0, S, H)$
   $(0, 1, \square, R , 1)$
   $(1, \square, 1, S, H)$
   $(1, 1, \square, R, 0)$
   
2. remove $b$'s, find first $a$ 
   $(0, a, \square, R, 1)$
   $(0, b, \square, R, 0)$
   $(0, \square, \square, S, H)$
   
   move first $a$ to end
   $(1, a, a, R, 1)$
   $(1, b, b, R, 1)$
   $(1, \square, a, L, 2)$
   
   go back to start, move to state 3 if we find a $b$. if we reach the start in state 2, halt
   $(2, a, a, L, 2)$
   $(2, b, b, L, 3)$
   $(2, \square, \square, S, H)$
   
   if we reach the start in state 3, repeat process
   $(3, a, a, L, 3)$
   $(3, b, b, L, 3)$
   $(3,\square, \square, R, 0)$

3. start by placing an $X$ 
   $(0, \#, \#, S, H)$
   $(0, \square, X, R, 1)$
   
   loop left and right placing $X$s until we find the $\#$
   $(1, X, X, R, 1)$
   $(1, \square, X, L, 2)$
   $(1, \#, \#, L, 3)$
   $(2, X, X, L, 2)$
   $(2, \square, X, R, 1)$
   $(2, \#, \#, R, 5)$
   
   if $\#$ is on the right, go to the left until we reach end of string then delete all the way to the head
   $(3, X, X, L, 3)$
   $(3, \square, \square, R, 4)$
   $(4, X, \square, R, 4)$
   $(4, \#, \#, S, H)$
   
    if $\#$ is on the left, go to the right until we reach end of string then delete all the way to the head
   $(5, X, X, R, 5)$
   $(5, \square, \square, L, 6)$
   $(6, X, \square, L, 6)$
   $(6, \#, \#, S, H)$
   
   
   
   