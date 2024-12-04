# Finite State Machines in Automata Theory

A Finite State Machine (FSM) is a mathematical model of computation used to simulate sequential logic, or, in other words, to represent and control execution flow. An FSM is defined by a list of its states, its initial state, and the conditions for each transition.

## Components of an FSM

An FSM consists of:

1. A set of states (S)
2. A set of input events (I)
3. A set of output events (O)
4. An initial state (S0)
5. A state transition function: F: S x I -> S
6. An output function: G: S x I -> O

## Types of FSMs

There are two types of FSMs: Mealy Machines and Moore Machines.

**Mealy Machines** produce outputs only in response to an input (i.e., output depends on both state and input). 

**Moore Machines** produce outputs based on states only (i.e., output depends only on the state).

## Example: A Simple Traffic Light System

Consider a simple traffic light system that switches between three states: Green, Yellow, and Red.

```python
class TrafficLightFSM:
    def __init__(self):
        self.states = ['Green', 'Yellow', 'Red']
        self.current_state = 'Red'

    def transition(self, input):
        if self.current_state == 'Red' and input == 'timer_elapsed':
            self.current_state = 'Green'
        elif self.current_state == 'Green' and input == 'timer_elapsed':
            self.current_state = 'Yellow'
        elif self.current_state == 'Yellow' and input == 'timer_elapsed':
            self.current_state = 'Red'

    def output(self):
        return self.current_state
```

In the above Python code snippet, the `TrafficLightFSM` class represents our FSM. The `transition` method represents the state transition function (F), and the `output` method represents the output function (G).

FSMs like the traffic light system can be used to model a wide range of systems in software engineering, from parsing text to designing embedded systems.