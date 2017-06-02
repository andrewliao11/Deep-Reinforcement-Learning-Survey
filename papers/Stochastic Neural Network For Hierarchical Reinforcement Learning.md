# Stochastic Neural Network For Hierarchical Reinforcement Learning

published in ***ICLR17***

## keypoints
- two phase: pretrain on swimmer with proxy reward, and then train on sparse reward environment 
- stochastic neural network of multi-modal policies, enabling weight sharing in different mode.
- information-theoretic regularizer: Mutural information, to **diversify** the skills, without this term as regularizer, 
the policy might perform very limited moves.
- similar to common HRL, they use a manager(somewhat like meta-controller) to determine which skills to perform.

## note
- advantage of stocahstic neural netowrk here: learn weight sharing itself. need not to pre-define number of skills.
- maybe the first RL paper to include the concept: use MI to diversify the policies
- strong experiment results on benchmark
