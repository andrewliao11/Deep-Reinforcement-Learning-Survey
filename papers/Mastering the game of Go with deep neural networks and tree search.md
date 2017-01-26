# Mastering the game of Go with deep neural networks and tree search
  
- David Silver, Aja Huang 
- First stage: supervised learning policy network, including rollout policy and SL policy network(learn the knowledge from human experts)
  -  Rollout policy is used for predicting **fast** but relatively inaccurate decision
  -  SL policy network is used for initialization of RL policy network(improved by policy gradient) 
- To prevent overfit, auto-generate the sample from self-play(half) and train with the KGS dataset(half)
- Use Monte Carlo tree search with policy network and value network. To understand the MCTS more, plz refer to [here](https://en.wikipedia.org/wiki/Monte_Carlo_tree_search#Principle_of_operation)
  - Selection: select the most promising action depends on Q+u(P) --> depth L
  - Expansion: after L steps, create a new child
  - Evaluation: evaluated by the mixture of value network and simulated rollout
  - Backup: Calculate and store the Q(s,a), N(s,a), which is used in Selection
