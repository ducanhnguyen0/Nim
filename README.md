# Nim: An self-learning AI 

Harvard CS50AI Project

## Description:

An AI program capables of teaching itself to play the 'Nim' game using Reinforcement Learning. A Q-Learning algorithm with ε-Greedy Decision Making is used to estimate the value of actions for game states.

## Tech Stack:

* Python

## Background:

Recall that in the game Nim, we begin with some number of piles, each with some number of objects. Players take turns: on a player’s turn, the player removes any non-negative number of objects from any one non-empty pile. Whoever removes the last object loses.

There’s some simple strategy you might imagine for this game: if there’s only one pile and three objects left in it, and it’s your turn, your best bet is to remove two of those objects, leaving your opponent with the third and final object to remove. But if there are more piles, the strategy gets considerably more complicated. In this problem, we’ll build an AI to learn the strategy for this game through reinforcement learning. By playing against itself repeatedly and learning from experience, eventually our AI will learn which actions to take and which actions to avoid.

In particular, we’ll use Q-learning for this project. Recall that in Q-learning, we try to learn a reward value (a number) for every (state, action) pair. An action that loses the game will have a reward of -1, an action that results in the other player losing the game will have a reward of 1, and an action that results in the game continuing has an immediate reward of 0, but will also have some future reward.

How will we represent the states and actions inside of a Python program? A “state” of the Nim game is just the current size of all of the piles. A state, for example, might be [1, 1, 3, 5], representing the state with 1 object in pile 0, 1 object in pile 1, 3 objects in pile 2, and 5 objects in pile 3. An “action” in the Nim game will be a pair of integers (i, j), representing the action of taking j objects from pile i. So the action (3, 5) represents the action “from pile 3, take away 5 objects.” Applying that action to the state [1, 1, 3, 5] would result in the new state [1, 1, 3, 0] (the same state, but with pile 3 now empty).

Recall that the key formula for Q-learning is below. Every time we are in a state s and take an action a, we can update the Q-value Q(s, a) according to:

`Q(s, a) <- Q(s, a) + alpha * (new value estimate - old value estimate)`

In the above formula, alpha is the learning rate (how much we value new information compared to information we already have). The new value estimate represents the sum of the reward received for the current action and the estimate of all the future rewards that the player will receive. The old value estimate is just the existing value for Q(s, a). By applying this formula every time our AI takes a new action, over time our AI will start to learn which actions are better in any state.

## Project Specification:

### get_q_value
The get_q_value function should accept as input a state and action and return the corresponding Q-value for that state/action pair.

### update_q_value
The update_q_value function takes a state state, an action action, an existing Q value old_q, a current reward reward, and an estimate of future rewards future_rewards, and updates the Q-value for the state/action pair according to the Q-learning formula.

### best_future_reward
The best_future_reward function accepts a state as input and returns the best possible reward for any available action in that state, according to the data in self.q.

### choose_action
The choose_action function should accept a state as input (and optionally an epsilon flag for whether to use the epsilon-greedy algorithm), and return an available action in that state.

## How to run

1. Clone this project
3. Run the NimAI Model allow it trains itself then play against it:
   ```
   python play.py
   ```
   (You can change the number of simulated games against itself in the train function)
