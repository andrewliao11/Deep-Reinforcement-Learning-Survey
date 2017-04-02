# One-Shot Imitation Learning
tl;dr

This work aims to do the one-shot (only one demonstration) imitation learning.

- Task Formalization:
The learned policy takes as input: (i) the current observation, and (ii) one demonstration that
successfully solves a different instance of the same task (this demonstration is fixed for the 
duration of the episode).
- training phase
given a pair of demonstration, a neural net is trained that takes as input **one demonstration** and the **current state**, and outputs an action with the **goal that the resulting sequence of states and actions matches as closely as possible with the second demonstration**.

## keypoints

## question

## basic concept
- imitation learning can be seperated into behavior cloning and inverse reinforcement learning
