## Glossary
**Individual**: any possible solution
**Population**: the group of all *individuals*
**Search Space**: all possible solutions to the problem
**Chromosome**/**Genotype**: blueprint for an *individual*; a particular set of genes in a genome
**Phenotype**: physical characteristic of the genotype (eg eye colour, height, etc)
**Trait**: possible aspect (*features*) of an *individual*
**Allele**: possible settings of trait (black, blonde, etc)
**Locus**: the position of a *gene* on the *chromosome*
**Genome**: collection of all *chromosomes* for an *individual* (usually only one)

## What are genetic algorithms?
Genetic algorithms are a formulated set of algorithms that use techniques inspired by evolutionary biology such as *selection, inheritance, mutation* and *crossover / recombination*. 

They are effectively a search technique that attempts to find true or approximate (sub-optimal) solutions (also categorised as *global search heuristics*).

Genetic algorithms are almost always implemented as a computer simulation. The simulation requires an initial population of abstract representations (chromosomes, the genotype or the genome) of candidate solutions (individuals or phenotypes) to some optimisation problem. That population then hopefully evolves towards better and better solutions.

Traditionally, the simplest forms of solutions are encoded in binary strings of 0s and 1s. Any arbitrary encoding is possible, but you then have to make sense of it.

1. The evolution starts from an initial population of **randomly** generated individuals and happens in successive **generations**. 
2. In each generation, the **fitness** of every individual in the population is **evaluated and ranked**. 
3. A number of individuals are **selected** from the current population (based on their fitness or ranking). 
4. These individuals are then **modified** (recombined/mated and possibly mutated) to form a new population (offspring + selected or just offspring).

This new population is then used in the next iteration of the algorithm. The algorithm terminates when
- a maximum number of generations has been reached
- a satisfactory fitness level has been reached

If the algorithm terminates due to a maximum number of generations, there is no guarantee a solution has been found.

## Chromosomes, genes, genomes, genotypes, phenotypes
![[Pasted image 20231009112541.png]]
![[Pasted image 20231009112557.png]]

## Requirements
A typical genetic algorithm requires two things to be defined:
1. a genetic representation of the solution domain (easy)
2. a fitness function to evaluate the solution domain (hard)

A standard representation is as an array of bits. Arrays of other types and structures can be used. The point is to have an array, as arrays are easily aligned due to their fixed size, which then makes all other operations (eg crossover) relatively trivial to do. Variable length representations may also be used, but crossover implementation is more complex, as are fitness calculations.

Chromosomes could be:

| Data Structure | Example |
|---|---|
|Bit strings|0101 ... 1100|
|Real numbers|43.2 -33.1 ... 0.0 89.2|
|Permutations of elements|E11 E3 E7 ... E1 E15|
|Lists of rules|R1 R2 R3 ... R22 R23|
|Program elements|genetic programming|
Or any other valid data structure...

The fitness function is defined over the genetic representation and measures the *quality* of the represented solution.  The fitness function is always problem dependant. For instance, in the *knapsack problem*$^1$, we want to maximise the total value of the objects that we can put in a knapsack of some fixed capacity.

A representation of a solution might be an array of bits, where each bit represents a different object, and the value of the bit (0 or 1) represents whether or not the object is in the knapsack. Not every such representation is valid, as the size of the objects may exceed the capacity of the knapsack.

The *fitness* of the solution is the sum of the values of all the objects in the knapsack if the representation is valid, and 0 otherwise.

In some problems, it is hard or even impossible to define the fitness expression; in these cases, interactive genetic algorithms are used.

## Basics of Genetic Algorithms
The most common type of genetic algorithm works like this:
1. a population is created with a group of individuals created randomly.
2. the individuals in the population are evaluated.
3. the evaluation function is provided by the programmer and gives the individuals a score based on how well they perform at a given task
4. two individuals are selected based on their fitness - the higher the fitness, the higher the chance of being selected.
5. these two individuals then "reproduce" to create one or more offspring, after which the offspring are mutated randomly
6. this continues until a solution has been found or a certain number of generations have passed.

### Initialisation
To begin with, many individual solutions are randomly generated to form an initial population. 

The population size depends on the nature of the problem, but typically contains several hundreds or thousands of possible solutions. Traditionally, the population is generated randomly, covering the entire range of possible solutions (the *search space*).

Occasionally, the solutions may be "seeded" in areas where optimal solutions are likely to be found.

### Selection
During each successive generation, a proportion of the existing population is selected to breed a new generation.

Individual solutions are selected through a *fitness-based* process, where fitter solutions (as measured by a fitness function) are typically more likely to be selected.

Certain selection methods rate the fitness of each solution and preferentially select the best solutions. Other methods rate only a random sample of the population, as this process may be very time-consuming.

Most functions are stochastic and designed so that a small proportion of less fit solutions are selected. This helps keep the diversity of the population large, preventing premature convergence on poor solutions. Popular and well-studied selection methods include roulette wheel selection and tournament selection.

### Reproduction
The next step is to generate a second generation population of solutions from those selected through genetic operators - crossover/recombination and/or mutation.

For each new solution to be produced, a pair of "parent" solutions is selected for breeding from the pool selected previously. By producing a "child" solution using the above methods of crossover and mutation, a new solution is created which typically shares many of the characteristics of its "parents".

New parents are selected for each child, and the process continues until a new population of solutions of appropriate size is generated. The processes ultimately result in the next generation population of chromosomes that is different from the initial generation.

Generally, the average fitness will have increased by this procedure for the population, since only the best organisms from the first generation are selected for breeding, along with a small proportion of less fit solutions.

### Crossover
The most common type is single point crossover. In single point crossover, you choose a locus at which you swap the remaining alleles from on parent to the other. 
![[Pasted image 20231009115608.png]]
As you can see, the children take one section of the chromosome from each parent. The point at which the chromosome is broken depends on the randomly selected crossover point.

This particular method is called single point crossover because only one crossover point exists. Sometimes only child 1 or child 2 is created, but often times both offspring are created and put into the new population.

Crossover does not always occur, however. Sometimes, based on a set probability, no crossover occurs and the parents are copied directly to the new population. The probability of crossover occurring is usually 60% to 70%.

### Mutation
After selection and crossover, you now have a new population full of individuals. Some are directly copied, and others are produced by crossover. In order to ensure that the individuals are not all exactly the same, you allow for a small chance of mutation.

You loop through all the alleles of all the individuals, and if that allele is selected for mutation, you can either change it by a small amount or replace it with a new value. The probability of mutation is usually between 1 and 2 tenths of a percent.

Mutation is fairly simple. You just change the selected alleles based on what you feel is necessary and move on. Mutation is, however, vital to ensuring genetic diversity within the population.
![[Pasted image 20231009115817.png]]

### Termination
This generational process is repeated until a termination condition has been reached. Common terminating conditions are:
- a solution is found that satisfies a minimum criterium
- a fixed number of generations is reached
- an allocated budget (computation time or money) is reached
- the highest ranking solution's fitness is reaching or has reached a plateau such that successive iterations no longer produce better results
- manual inspection
or any combinations of the above.

## Symbolic AI vs Genetic Algorithms
Most symbolic AI systems are very static. Most of them can usually only solve one given specific problem, since their architecture was designed for whatever that specific problem was in the first place.

Thus, if the given problem were somehow to be changed, these systems could have a hard time adapting to them, since the algorithm that would originally arrive to the solution may be either incorrect or less efficient.

Genetic algorithms (or GA) were created to combat these problems; they are basically algorithms based on natural biological evolution.

The architecture of systems that implement genetic algorithms (or GA) are more able to adapt to a wide range of problems. 

A GA functions by generating a large set of possible solutions to a given problem. It then evaluates each of those solutions, and decides on a "fitness level" for each solution set. These solutions then breed new solutions.

The parent solutions that were more "fit" are more likely to reproduce, while those that were less "fit" are more unlikely to do so.

In essence, solutions are evolved over time. This way you evolve your search space scope to a point where you can find the solution. Genetic algorithms can be incredibly efficient if programmed correctly.


[1]: In the knapsack problem, **you need to pack a set of items, with given values and sizes (such as weights or volumes), into a container with a maximum capacity**. If the total size of the items exceeds the capacity, you can't pack them all. https://en.wikipedia.org/wiki/Knapsack_problem