## rl

### Bandit Problem
We have k-arms in a setup to pull and obtain reward. Each arm has a _latent_ probability distribution from which it samples the reward when pulled. The probability
distribution can be stationary or it can change over time. Our goal is to maximize cumulative rewards obtainedd over a period of time or a number of pulls i.e, find
the optimal action `a_*` as soon as possible and keep exploiting it.

Note that if the rewards for each arm were deterministic, then a simple iteration (`exploration`) over k-arms would suffice to find the max-reward arm and for the 
rest of the remaining time just keep pulling (`exploiting`) that arm. But the rewards are stochastic in nature.

This is a simplified RL setup, where the agent repeatedly sees the same `state` (i.e., same k-armed bandits to pull form) to `act` (choose one to pull). Also note
that the optimal action (`a_*`) at each step is same (the action with highest expected reward) since there is no state dependence.
There are
2 kinds of algorithms based on how they choose to make the decision:
1. By estimating values of an action `q_*(a) = E[R_t | A_t = a]` using sample averages `Q_t(a)`. Eg. epsilon-greedy, UCB etc.
2. By assigning numerical preferences to actions $H_t(a)$ and updating (`gradient ascent`) it according to `dE[Rt] / dHt(a)`. Eg. Gradient Bandit algorithm.
This defines a prob. distribution `pi(a)` over the actions to pick one.

Regret equation: At time step t, `total regret = t x q_*(a_*) - (R1 + R2 + ... + Rt)` i.e., the difference between optimal rewards at each step and the actual
reward obtained (based on possible sub-optimal action chosen.)

Advanced: There are other variations of the bandit problem. One that I am particularly aware, is the `pure-exploration bandit problem` and an algo. to solve 
it [KL-LUCB](http://proceedings.mlr.press/v30/Kaufmann13.pdf) (I can't make anything out of this cryptic paper though!) as used in 
[Anchor](https://homes.cs.washington.edu/~marcotcr/aaai18.pdf) paper.
