# Reinforcement Learning

## What is RL?
Sequential decision making processes -> how to sequentially interact with environment to maximize long-term objective

Key features: 

- learns best action by trial and error
- reward can be delayed
- might have to sacrifice immediate reward to gain more long-term reward


vs. supervised learning: 

- learning to do vs. learning to predict
- decisions influence next input

## Formalization
Markov Decision Process (with assumption observation = state)

**Elements**  

- finite set of states s ()
- finite set of actions for each state 
- dynamic function: probability of going to state s' given state s
- reward function
- discount factor

Assumptions:

- discrete time steps
- next state only depends on current state and action
- rewards only depend on state, action, and next state


**Policy** 

- mapping from state to action, given state, what action should be taken?
- Goal: find policy that maximizes sums of rewards

There is no objective goodness of state, always depends on policy (future actions)

**Value functions**
Measures how good a policy is = expectation of future sum of rewards (at each state) 

Formally: Expected return (discountet sum of rewards) given state s


## How to find optimal policies

from data:

- learn value function (expected sum of discountet future rewards) = expectation of how good the future is
- lean q value function

then derive policy from there -> follow action with highest q value


or directly try to find the policy

or try to learn a model that predicts environment (i.e. model that predicts the next state form state action pair, and 
reward)


## Non MDPs

- partially observable
- multi-agent problems
- bandit -> because actions you take now, don't influence what happens in the future




