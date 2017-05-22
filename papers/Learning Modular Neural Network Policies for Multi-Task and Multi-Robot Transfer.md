# Learning Modular Neural Network Policies for Multi-Task and Multi-Robot Transfer

This paper aims to solve multi-robots, multi-tasks **modular** policy. Before, modular network is frequently 
used in question answering task, see [@Jacob Andreas](https://people.eecs.berkeley.edu/~jda/). This paper introduce 
a nice characteristic of modular network, composing network in a plug&play-like fashion.

## Problem formulation
- define a universe that contains robots:R_1, R_2 and tasks:T_1, T_2. There are 4 different permutations in the universe.
The algorithms wants to do the zero-shot transfer from the 3 combination[(R_1, T_1), (R_1, T_2), (R_2, T_1))] to the 
unseen combination[(R_2,T_2)]

## Keypoints
- Need to robots modules to be **task-invariant** and task modules to be **robot-invariant**
- Apply bottleneck and dropout on the interface of the module to prevent one module overfitting on some specific modules
- Allow changes in observation/action space
- Few training steps to tranfer (few-shot learning)

## Some opinions
- really cool ideas and worth exploring more
- lack of implementation details 
- the authors choose a good environment to show off their paper (from easy to difficult)
- in QA task, program generator matters a lot! In this [Modular Multitask Reinforcement Learning with Policy Sketches]
(https://arxiv.org/abs/1611.01796), they use human-defined policy sketch. In the near future(maybe nips2017), we can expect 
someone doing modular RL with program generator jointly trained.
