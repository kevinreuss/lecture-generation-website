# Genetic Algorithms in Optimization

Genetic Algorithms (GAs) are inspired by natural evolution and used for optimization problems. They use techniques such as mutation, crossover (recombination), and selection.

Here's a high-level overview of a GA:

1. **Initialization**: Start with a population of randomly generated solutions.
2. **Selection**: Evaluate the fitness of each individual in the population.
3. **Crossover**: Select a pair of parent solutions and combine them to form new offspring.
4. **Mutation**: Randomly alter some genes in the new offspring.
5. **Replacement**: Replace least fit individuals in the population with the new offspring.

Let's illustrate with a simple Python implementation of a GA for the problem of maximizing the function `f(x) = x^2`.

```python
import random

# Fitness Function
def fitness(x):
    return x*x

# Initial Population
population = [random.randint(-100,100) for _ in range(100)]

for generation in range(1000):
    population = sorted(population, key = fitness, reverse = True)
    
    # Crossover
    for i in range(20, 100):
        parent1 = random.choice(population[:20])
        parent2 = random.choice(population[:20])
        child = (parent1 + parent2) / 2 + random.uniform(-10,10)
        population[i] = child
    
    # Mutation
    for i in range(20, 100):
        if random.uniform(0,1) < 0.1:
            population[i] += random.uniform(-10,10)
```

In the code, the fitness function is `x^2` that we want to maximize. The population is initialized with 100 random integers. The top 20 individuals (those with the highest fitness) are allowed to breed. The offspring replace the bottom 80 individuals in the population. There's also a 10% chance that an individual will undergo mutation. 

The GA will run for 1000 generations, and hopefully, the individuals in the final population will be close to the optimal solution of the problem.

This is a simplified example. In practice, GAs are used for more complex optimization problems, and there are many variations and enhancements to the basic algorithm.