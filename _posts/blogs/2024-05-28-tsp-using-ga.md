---
layout: post
title:  "Analysis of Crossover Techniques for Solving the Travelling Salesman Problem using a Genetic Algorithm"
date:   2024-05-28 21:55:37 -0400
tags: tsp ga algorithms artificial-intelligence
---
## Introduction 

{% raw %}
The Travelling Salesman Problem (TSP) is an NP-hard problem in
combinatorial optimizaiton. \
It asks: 'Given a set of N cities, find the shortest tour, such that
the Travelling Salesman can visit all the cities without having to go to
each city more than once.'

Determining an exact solution by Checking every possible tour for a TSP
with a large number of nodes is difficult, as the worst-case runtime
complexity is $O(n!)$. The fastest exact algorithms can solve the problem
in time $O(n^2 2^n)$.

Heuristic and approximation algorithms trade-off accurate results for a
faster execution time.

One metaheuristic algorithm to solve the TSP is the Genetic Algorithm.

The Genetic Algorithm emulates the process of biological evolution.
The algorithm begins with by initializing a population. This can be random
or use an educated guess / approximation of the ideal individual.
The population is evaluated against a fitness function or objective function.
The best indivviduals are then selected according to a selection ratio and
a crossover operation is performed to generate a new population.
This process is repeated until an exit condition is met.

{% endraw %}

The Pseudocode for the Genetic Algorithm is:
{% highlight python %}

population = initialize_population()
while evolution:
    fitness = fitness_function(population)
    population = crossover(population, fitness, selection_ratio)

{% endhighlight %}
{% raw %}

The Genetic Algorithm poses a few interesting choices for implementation
to solve the TSP, which are discussed below.

## Tour Representation

A flexible method of encoding a tour is by using a list of indices.
The nodes are stored in an array, with each element in the tour referring
to the index of the respective node.

## Initial Population

The Initial Conditions to start the 

The Initial population can be generated in two ways:

1. Randomized Population
2. An Educated Guess


{% endraw %}

## Crossover


## How are the Results Generated?
 

## Resources Used (Change Later)

[Travelling Salesman Problem using Genetic Algorithm](https://d1wqtxts1xzle7.cloudfront.net/81272325/dristi1007-libre.pdf?1645595806=&response-content-disposition=inline%3B+filename%3DTravelling_Salesman_Problem_using_Geneti.pdf&Expires=1716577616&Signature=C64weczGe7DLh4W2bKYN~0TkYIr0mJbDkr7lwzd7cPYhnsNIxsn2IRJyqhVOSZv4L-JCBaOjghiztfsWg~Cmdbif1eSDrtugrDnZdJ6X40IFlt2LZCZUtFlQiYTX2iP6yNxdyhdFpKqCN72jrNysvrmAEGf3RWmp-ehc9oYvXj8Lpp73dXwLgI9oOp1esBV6uGoPsryOLgfF5gSPwPlohF7-MUncykz2fOVnchRkHHXR3pBX4Kmv1DSn85BewCtnAjQyJ8HZYEoJdH1va0ZMwIaIVpwilLpIcmRFYxR868-iCqJebE8fLGtZlFAWzVz8-hwgfA7Dz1MGCfyTfnTZKw__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA)

[On Solving Travelling Salesman Problems by Genetic Algorithms](https://link.springer.com/chapter/10.1007/BFb0029743)

[Crossover Operators in Genetic Algorithms: A Review](https://www.researchgate.net/profile/Padmavathi-Kora-2/publication/315175882_Crossover_Operators_in_Genetic_Algorithms_A_Review/links/59c6105d458515548f2f3b5f/Crossover-Operators-in-Genetic-Algorithms-A-Review.pdf)

## Implementation or TODO List

- [x] Compare Population Initialization Methods
  - [x] Random (Currently Implemented)
  - [x] Nearest Neighbor
  - [x] Implement as many TSP approximation methods as possible

- [x] Crossover Methods
  - [x] Ordered Crossover (OX)
  - [x] Partially Mapped Crossover (PMX)
  - [x] Cycle Crossover (CX)
  - [ ] Edge Recombination Crossover (ERX)

- [x] Library Parser
  - [x] Extract Graph from tsplib [git repo](https://github.com/mastqe/tsplib.git)

- [ ] Testing
  - [ ] Initialization Methods: Random vs. Nearest Neighbor
  - [ ] Crossover Methods: OX vs. PMX vs. CX vs. ERX
  - [ ] OX better when randomized every time vs. once per generation?


- [ ] Figures Needed to Create
  - [ ] Demonstration of each Crossover Method
