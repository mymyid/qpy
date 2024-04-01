# qpy

Q-learning is a value-based reinforcement learning algorithm that learns the quality of actions, denoting the total expected rewards an agent can obtain, starting from a state and taking an action. Here's a simplified overview of how to implement Q-learning:

1. **Initialize the Q-table**: This is a matrix where we have a row for every state and a column for every action. The value at Q(s, a) represents the current estimate of the total reward you can get, starting from state `s` and taking action `a`. Initialization is typically done with zeros.

2. **Choose an action**: From the current state, select an action. This can be done randomly (exploration) or by taking the best-known action (exploitation), according to the Q-table. A common strategy is the ε-greedy method, where with probability ε, a random action is chosen (exploration), and with probability 1-ε, the action with the highest value in the Q-table is chosen (exploitation).

3. **Perform the action and observe the reward**: Once an action is taken, the agent receives a reward and transitions to a new state.

4. **Update the Q-table**: Use the Bellman equation to update the Q-value for the state-action pair. The update is a form of moving the Q-value closer to the new estimate:
   
   ```
   Q(s, a) = Q(s, a) + α * (r + γ * max(Q(s', a')) - Q(s, a))
   ```
   Where:
   - `Q(s, a)` is the current Q-value,
   - `α` is the learning rate,
   - `r` is the reward received for taking action `a` in state `s`,
   - `γ` is the discount factor, representing the importance of future rewards,
   - `max(Q(s', a'))` is the estimated optimal future value, achieved by taking the best action `a'` in the new state `s'`.

5. **Repeat steps 2-4 for each episode**: Continue this loop for a fixed number of episodes or until the agent's performance is satisfactory.
