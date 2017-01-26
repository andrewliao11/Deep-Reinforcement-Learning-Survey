# Human-level control through deep reinforcement learning

- Most optimization algorithms assume that the samples are independently and identically distributed,
      while for reinforcement learning, the data is a sequence of action, which breaks the assumption.
- Strong correlation btn data => break the assumption of stochastic gradient-based algorithms(re-sampling)
- Experience replay(off-policy)
- Iterative update Q-value
- [Source code [Torch]](https://sites.google.com/a/deepmind.com/dqn)
