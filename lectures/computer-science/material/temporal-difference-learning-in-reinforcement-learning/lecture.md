# Temporal Difference Learning in Reinforcement Learning

Temporal Difference (TD) Learning is a type of Reinforcement Learning (RL) that combines the ideas of Monte Carlo methods and Dynamic Programming. It provides a way to estimate the value function without knowing the full model of the environment, unlike Dynamic Programming. Simultaneously, it updates estimates based on other estimates, unlike Monte Carlo methods.

## TD(0) Learning Algorithm

The simplest TD learning algorithm is TD(0). Let's assume we are trying to estimate `v(s)`, the value of a state `s`. In each time step, the agent observes the current state `s`, takes an action `a`, receives a reward `r`, and observes the new state `s'`. The value `v(s)` is updated using the observed reward and the estimated value of the new state `s'`.

Here's the update rule in TD(0):

```python
v(s) = v(s) + alpha * (r + gamma * v(s') - v(s))
```

Where:
- `alpha` is the learning rate.
- `gamma` is the discount factor.

## TD Learning vs Monte Carlo

The key difference between TD Learning and Monte Carlo methods is in how they update the value function. 

Monte Carlo updates are based on the total actual return of an episode, whereas TD Learning updates are based on the estimated value of the next state. This makes TD Learning bootstrapping - it updates estimates based on other estimates.

Let's look at the update formulas for both:

Monte Carlo:
```python
v(s) = v(s) + alpha * (G - v(s))
```

TD Learning:
```python
v(s) = v(s) + alpha * (r + gamma * v(s') - v(s))
```

Here, `G` is the actual return. 

In TD Learning, `r + gamma * v(s')` is a biased estimate of `G`, but it's available at each time step. This lets TD methods to learn in an online, incremental fashion.

## SARSA and Q-Learning

Two popular algorithms that extend TD Learning to action-value functions are SARSA (State-Action-Reward-State-Action) and Q-Learning. They use similar update rules, but Q-Learning is off-policy (it learns the value of the optimal policy regardless of the agent's actions), while SARSA is on-policy (it learns the value of the policy being followed).

SARSA:
```python
Q(s, a) = Q(s, a) + alpha * (r + gamma * Q(s', a') - Q(s, a))
```

Q-Learning:
```python
Q(s, a) = Q(s, a) + alpha * (r + gamma * max_a' Q(s', a') - Q(s, a))
```

In both cases, `(s, a, r, s', a')` is a tuple representing a transition in the environment.

In summary, Temporal Difference Learning is a powerful tool in the RL toolbox, bridging the gap between Monte Carlo methods and Dynamic Programming, and enabling efficient, incremental learning.