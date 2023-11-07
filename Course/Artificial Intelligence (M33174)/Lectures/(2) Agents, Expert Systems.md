**Percept:** The agent's current view of the environment's state
An action chosen may be the result of the combined input sequence or percept sequence up to the point of the action. 

**Fixed strategy systems:** systems that *do not learn*.
These work by confining the AI system to an area of knowledge that a particular export in a particular subject might have (eg a doctor writing rules for a medical system).

It is generally easier to create systems that solver particular problems than systems that solve problems in general.

**The heuristic approach**
An algorithm is a list of computer instructions that, given the correct input, will always produce the correct output. However, many of the problems we want to solve cannot be solved on any computer in our lifetime. These are $NP$ problems.

$P$ problems can be solved in "polynomial time", meaning the time they take is a polynomial function of some program measure. These are the normal problems we come across when we design programs.

$NP$ problems cannot be solved in polynomial time, but have a solution that can be guessed at and verified in polynomial time instead. $NP$-hard problems are a subclass of the $NP$ problems that represent the most extreme cases

In this case, we use the knowledge we have about the problem (expertise) to devise a program that will get close to the solution to the problem most of the time. We usually represent knowledge as a set of rules.

A rule that gets us closer to the solution is called a *heuristic*.

To solve a problem we would have to evaluate every possible input combination starting from the initial configuration. This can be illustrated using a "tree search algorithm" by trying all possible actions.
![[Pasted image 20231003162733.png]]

Each layer of the search tree is called a "ply" and the depth of search is often called "one ply" or "three ply" searches.

A tree search algorithm might be useful in some simple tile problems, for instance a small board or if the starting position is close to the final answer. However, it would not scale up to larger boards that were scrambled to a higher degree without absorbing more and more computer time and memory.

To solve this rationally and without absorbing all the computer resources our computer program (agent) will need to make rationale moves based on simpler (more simple than a complete search) evaluations.

Our first simple automatic solution to the tile program may be to select a move at random. A simple "Markov chain" can be used - a chain of moves selected from a number of possibilities according to some probability distribution.

In order to improve our algorithm, we need to remove the random element from our program. For example, "select the move that takes the board tile arrangement cloesr to the desired arrangement".

**Lessons from our program**
We can incorporate our knowledge of the system into a set of rules:
- if the state of the world is $a$ and $b$, then take $x$ and $y$ action
  this can be rewritten as "if antecedent then consequent"
- we need measures of the environment
- we require a detailed knowledge of the system or environment we are working in

**Expert systems**
This is the original method of creating what was referred to as an expert system that used a significant amount of Task Specific Knowledge. Anything that requires a lot of problem specific knowledge about a restricted domain is referred to as a Strong Method in AI speak.

The expert agent has drawbacks:
- knowledge may take up a lot of memory and be expensive to set up
- the knowledge base may require significant testing and updating
- the knowledge base may be "brittle" or too large to write down
- the knowledge base may be too large to search effectively
Conclusion: Task Specific Knowledge is NOT cheap.

**Agents that learn and adapt**
These methods use little knowledge about the task (they are known as Weak Methods) but use methods that allow them to learn or adapt to the problem eg adaptive search, neural networks, swarm intelligence

They do have drawbacks too:
- difficult to understand or interpret what has been learnt
- difficult to predict their stability or outcome
- difficult to deduce the required structure for the particular problem
However, these methods are the subject of intensive research because it is felt that they include some of the key abilities required of the intelligent rational agent.

**Intelligent problem solving and intelligent agents**
One way of thinking of this is to supply the intelligent agent with the ability to react dynamically as information about solving the task is obtained. Its ultimate behaviour should be based on its experience, otherwise it lacks autonomy. The expert system alone is not appropriate in a dynamic world, thus the agent should be an amalgamation of the strong and weak methods.

An intelligent agent is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through effectors to achieve goals eg robots, humans, software. Thus, our rational agent:
- does the right thing (not necessarily the human thing)
- does what is required to make itself successful (adapts according to experience)
- adapts to meet goals using a performance measure or. credit assignment

The structure of an agent includes the Architecture and the Program.
The agent program consists of:
- Function: *Skeleton Agent* (percept) *Returns* (action)
- Static Memory: the agent's memory of the world
- Memory: *Update-Memory* (memory, percept)
- Action: *Choose-best-Action* (memory)
- Action: *Memory-Update-Memory* (memory, action)
- Return Action

Some examples of intelligent agents include:
![[Pasted image 20231009110323.png]]

There are several types of agents depending upon the autonomy the designer wishes to build in. The simplest type is our expert system.

**Simple Reflex Agent**
This agent takes information in from a sensor, compares it to the knowledge base, and performs an action accordingly. Simple agents allow for these actions to be executed quicker. An example of this is 'if car in front is braking, then brake'
![[Pasted image 20231009110643.png]]
The agent attempts to keep track of the world because its sensors do not provide complete access to the world state (just as our knowledge of our world is used by us to create a picture of the world, even though our sensors do not tell us everything)

Hence, the agent
- needs to know how the world evolves
- needs to know how its actions affect the world
- can take better actions based on the two prerequisites above

**Goal Based Agent**
![[Pasted image 20231009110955.png]]
The goals generate actions or reconstruct a condition-action set. These goals are not necessarily preset (similar to humans, our actions are determined by our goals and their priority - as various emotions in humans allow us to choose between or change goals).

Hence, the agent should
- choose the best decision among a number of alternatives depending upon it goals
- be more flexible in complex environments 
- generate new behaviour by specifying new or different goals

**Utility Based Agent**
![[Pasted image 20231009111231.png]]
Goals are not enough to generate high quality behaviour. A more general performance measure should allow for the comparison of different world states (similar to humans choosing between goals based on prediction of success and risk).

- If there are conflicting goals, the utility knowledge can specify the necessary trade-offs
- If several goals are possible, the utility knowledge provides a method of weighing up the likelihood of success against the importance of the goals
The addition of utility makes complex rational decisions possible.

