# Learning Tetris Using the Noisy Cross-Entropy Method

the paper works on solving Tetris with modified cross entropy method. original CE method in reinforcement learning usually results in early convergence.

### Cross entropy method in reinforcement learning
- first we start with a random uniform distribution ```F_0```
- drawn from ```F_0``` and get N samples θ_0, θ_1, ...
- choose the top K samples that get the highest scores and use these selected sample(θ_0, θ_1, ...) update distribution and get ```F_1```


## keypoints
- add noise to the cross-entropy method to prevent early converge
- if we decrease the noise, which is only depend on time steps, the performance can even be better.
- noise :point_right: prevent early converge

## note
- can view the noise apply to std as ensure enough exploration

## implementation
I have a simple implementation on CartPole, [link](https://gist.github.com/andrewliao11/d52125b52f76a4af73433e1cf8405a8f)
