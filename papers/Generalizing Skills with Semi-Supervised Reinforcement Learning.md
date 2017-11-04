# Generalizing Skills with Semi-Supervised Reinforcement Learning

Chelsea Finn, Tianhe Yu, Justin Fu, Pieter Abbeel, Sergey Levine

## keypoints
- Train RL agent under reward MDPs and no-reward MDPs
- for no-reward MDPs: using guided cost learning (finn. 2016)
	- IRL: re-optimizing policy under novel environment (allow interaction with no-reward MDPs)
-  for RL: using guided policy search; for IRL: using guided cost learning

## related to IRL
- ill-defined problem: no exact solution. There are many reward functions can explain optimal policy.
- suffer reward ambiguity