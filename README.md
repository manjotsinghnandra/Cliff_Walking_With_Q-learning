# Q Learning on Cliff Walking Environment

## Overview

This project implements the Q Learning algorithm using the Cliff Walking environment from Gymnasium. The agent learns an optimal policy through trial and error by interacting with the environment and updating a Q table based on received rewards.

The goal is to navigate from the start position to the goal while avoiding the cliff cells that result in large negative rewards.

## Environment

Environment: CliffWalking-v1

State Space:
48 states representing positions in a 4x12 grid.

Action Space:
4 actions

0 = Up
1 = Right
2 = Down
3 = Left

## Algorithm

The implementation uses Q Learning with an epsilon greedy exploration strategy.

Parameters:

Gamma (discount factor): 0.99

Learning rate (alpha): 0.5

Exploration rate (epsilon): 0.1

Training episodes: 500

Q Update Rule:

Q(s, a) = Q(s, a) + α [r + γ max Q(s', a') - Q(s, a)]

## Training Process

For each episode:

1. Reset the environment.
2. Select actions using epsilon greedy policy.
3. Execute actions and observe rewards.
4. Update Q values using the Q Learning update rule.
5. Continue until the episode terminates.
6. Store learned values in the Q table.

The environment is rendered every 50 episodes to visualize the agent's behavior.

## Results

During training, the agent gradually improves its performance.

Early episodes produce very large negative rewards because the agent frequently falls into the cliff.

As training progresses:

- Episode length decreases.
- Total reward improves.
- The agent learns a near optimal path.

Final evaluation:

Total Reward: -13

Episode Length: 13

This indicates that the agent successfully learned the shortest safe route to the goal.

## Learned Policy

The learned Q table contains the estimated value of taking each action from every state.

Example:

State 36:

```
[-12.2479, -112.1254, -13.1254, -13.1254]
```

The extremely low value for moving right shows that this action leads into the cliff and is heavily penalized.

State 35:

```
[-2.9700, -1.9899, -1.0000, -2.9701]
```

The highest value corresponds to the best action from that state.

## Requirements

Python 3.x
Gymnasium
NumPy

## Conclusion

This project demonstrates how Q Learning can learn an effective navigation strategy in a reinforcement learning environment. Through repeated interaction with the Cliff Walking task, the agent learns to avoid dangerous states and reach the goal efficiently using a learned Q table.
