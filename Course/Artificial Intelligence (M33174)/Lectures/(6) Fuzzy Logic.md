#### Fuzzy membership
Membership function $M(x)$ represents the degree of belief (confidence factor) that $x$ belongs to some category. $$0 \leq M(x) \leq 1 \:\text{or}\: blah$$
#### Fuzzy sets
A set of fuzzy variables (categories) is called a fuzzy set. For example, an income can be {small, medium, high}.

Each category in the set has its own membership function. The peak of each function when plotted is 1 (from 0).

These membership functions may have intercepts.
![[Pasted image 20231204162820.png]]

##### Reasoning with fuzzy rules
Reasoning with fuzzy facts with different degrees of membership (confidence) $$\begin{split} M(\not x) &= 1 - M(x) \\ M(x_1 \land x_2) &= \min[M (x_1), M (x_2)] \\ M(x_1  \lor x_2) &= \max[M (x_1), M (x_2)] \end{split}$$
In a fuzzy logic system ALL rules are firing in parallel. This means that we can have multiple conclusions about the same fact, or even contradictory conclusions.

If two rules arrive to the same conclusion $x$ with different $M_1(x)$ and $M_2(x)$ then we use a formula to combine the beliefs $$M(x) = M_1(x) + M_2(x) - (M_1(x) \times M_2(x))$$ For example, let $M_1 = 0.2, M_2 = 0.6$ that the risk is low, then $M = 0.2 + 0.6 - (0.2 \times 0.6) = 0.68$.

Different and even contradictory conclusions (eg risk is low and high) are all allowed to stay in the system.

### Defuzzyfication
The conclusions that a fuzzy reasoning system will arrive to are called 'fuzzy facts' (facts with degrees of membership). For example, risk is low with $M = 0.5$.

The outcome, however, must be a precise decision. The process of converting a fuzzy fact into a crisp value is called defuzzyfication. 

The best way of defuzzyfication is called the centroid method (or finding the 'centre of gravity').
![[Pasted image 20231204165226.png]]
*(Unite and select the areas under the belief values $\mu(y)$. The centre of the selected area provides the crisp output value.)*

#### Strengths & Weaknesses
Strengths:
- use fewer rules as there is no need to cover all the cases
- thus, it is easier to understand the system
- fine tuning by changing the membership functions

Weaknesses:
- limited explanatory system
- still necessary to consult experts
- saturation problem (if memberships are not defined carefully)