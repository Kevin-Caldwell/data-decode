---
layout: post
title:  "Solving the Travelling Salesman Problem with the Genetic Algorithm"
date:   2024-05-07 21:55:37 -0400
tags: tsp ga algorithms artificial-intelligence
---

# Motivation

{% raw %}
The Travelling Salesman Problem states: 
'Given a set of N cities, find the shortest tour, such that
the Travelling Salesman can visit all the cities without 
having to go to each city more than once.'

In my case, the inputs to a solver consists of a n by n matrix, containing 
elements $$a_{ij} = E(P_i, P_j)$$, where $$E(P_1,P_2)$$ is an energy function 
which returns the distance between the cities at points $$P_1$$ and $$P_2$$.

Exact algorithms do not scale nicely when the number of cities is 
increased. One particular exact algorithm, is evaulating every 
permutation, and keeping track of the shortest tour. As there are 
$$n!$$ permutations for $$n$$ cities, the time complexity is $$O(n!)$$.

Python Code for this Algorithm is given below:
{% endraw %}

{% highlight python %}
def tsp_permute(
    distance_matrix: np.array, start: int, point_count: int, eval_fcn: callable
):
    """Search through every permutation of paths to determine the optimal solution."""
    # Initialize a default solution
    best_path = np.linspace(0, point_count - 1, point_count, dtype=int)
    shortest_distance = eval_fcn(best_path, distance_matrix)

    # itertools.permutations imported from iter, loops through all permutations of list
    for permutation in itertools.permutations(best_path):
        # Filter for permutations starting with the start index
        if permutation[0] == start:

            distance = eval_fcn(permutation, distance_matrix)
            # Update Lowest if distance is lower than current lowest
            if distance < shortest_distance:
                best_path = permutation
                shortest_distance = distance

    return best_path
{% endhighlight %}
{% raw %}

To reduce the time complexity required to find a reasonable solution, 
Approximate Solutions are used, one of which is the **Genetic Algorithm**.

# The Genetic Algorithm

The Genetic Algorithm is a general purpose approach for finding the minima 
of a function $$f(x)$$. 

1. It starts by generating an *initial population* of solutions, given by 
$$ \{ x_0^0, x_1^0, ..., x_n^0 \} $$
2. It evaluates the fitness of each solution in the population
3. Select parents which can cross-over for a new generation
4. Mutating the genes of the Parents to get a new population
5. Repeat Step 2 as necessary, usually up to a fixed number or till improvement is negligible

# Implementation Details

My implementation is somewhat naive, and although largely unoptimized, it demonstrates the 
trends expected for TSP solutions using the Genetic Algorithm. 

Each tour is represented by a list of cities, starting with the initial location of the salesman. 
A cyclic path is assumed, with the last city in the list being connected to the first city.

The *Fitness Function* returns the energy required to complete the path. A lower value corresponds 
with higher fitness. 

The *Genetic Variety* is a parameter related to the selection ratio 
(Selection ratio = Genetic Variety / Population Size). It determines the number of solutions 
allowed to cross-over into the next Generation.

The *Initial Population* is a list of n randomized tours, obtained by shuffling a default tour.

{% endraw %}