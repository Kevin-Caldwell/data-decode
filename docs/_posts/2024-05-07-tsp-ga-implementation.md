---
layout: post
title:  "Solving the Travelling Salesman Problem with Genetic Algorithms"
date:   2024-05-06 21:55:37 -0400
categories: tsp ga algorithms artificial-intelligence
---

# Motivation

The Travelling Salesman Problem states: 
'Given a set of N cities, find the shortest tour, such that
the Travelling Salesman can visit all the cities without 
having to go to each city more than once.'

In my case, the inputs to a solver consists of a n by n matrix, containing 
elements $a_{ij} = E(P_i, P_j)$, where $E(P_1,P_2)$ is an energy function 
which returns the distance between the cities at points $P_1$ and $P_2$.

Exact algorithms do not scale nicely when the number of cities is 
increased. One particular exact algorithm, is evaulating every 
permutation, and keeping track of the shortest tour. As there are 
$n!$ permutations for $n$ cities, the time complexity is $O(n!)$. 

Python Code for this Algorithm is given below:

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

To reduce the time complexity required to find a reasonable solution, 
Approximate Solutions are used, one of which is the **Genetic Algorithm**.

# The Genetic Algorithm

WIP
