# SQL-GYM-HER-TRADING
Data not included.

Testing the HER Algorithm in the "Test" folder.
Utilizing the HER-Trading Env with the HER-Algorithm in the "Main" folder.

The concept and revelation that inspired the reinterest in this particular algorithm is mainly due to the reward function. HER functions by encountering a 0 which symbolizes a positive reward that ends the episode. The reward function then creates a reward trajectory based off the path it took. For robotic arm tasks, this is simply a plug and play. For a stochastic random, nonlinear environment such as a stock market, the algorithm would prove to be far more advanced than originally thought.

The Zero Profit Condition inspired this new reward function scaled for the stock market. 
Lets say the robatic arm fails. The reward function idea in HER is to imagine as if that was the goal all along. It receives a positive reward for achieving that goal. So we end up with a positive reward, from a negative experience.
When a robotic arm finishes its task. It saves the final state. And aims to achieve this state in the future.

In HER, there are specified goals that can be achieved which result in rewards of 0. The idea is to play back the different state-action-reward-goal pairs and learn which goal suits the best state.

Anyways, to apply this zero sum game to the stock market. We simply apply the following reward schema
Reward = Profit - (commissions + oppurtunity_cost)
Reward = Profit - (commissions + desired_profit + -Profit)
This ensures that a loss would be experienced negatively and any form of profit past commisions would be a completed goal.

This idea may not fease well for maximizing reward and minimizing loss such as algorithms like PPO. Which tends to perform better in my opinion for arbitrage than HER.

However, for a highly sample efficient algorithm: HER makes it possible to optimize strategies in order to complete the task.
The idea is to see how well it will perform at generating a low loss, high-winrate algorithm.

Generally in PPO, the algorithm receives losses as a reward and propogates that reward through the network.
with HER, the off policy algorithm aims to achieve the reward given any state.

Therefore similiar to a robotic arm picking up a cube placed in a random location.
An HER algorithm should be able to create a strategy that is only "learned" when it experiences a low losses, and higher winrates.
The idea with the reward shaping as well is that any forms of losses could be treated as potential wins.
