# Noisy Networks for Exploration

The authors propose an idea to perturb in parameter space for exploration. Replacing the epsilon-greediy method, 
the perturbation in parameter space is learned by gradient descent along with other weights. There are some heuristic 
methods to do the exploratoin, e.g. optimism initailization, epsilon-greedy(perturb in action space). However, 
these method often work well only on small state space. The paper evaluate their method on value-based and policy-based
algorithms, and both get a bunch of improvement.

## keypoint
- Do the pertubation on parameter space for exploration
- Universal idea for most of the RL algorithms (empirically found)
- The scale of the perturbation is learned along with the original objective function (easy to apply)

## notes/questions
-  The author doesn't provide much therodical proof or intuitive of the proposed method thought the result is good.
-  It'll be good for the author to visualize the (behavior) difference between epsilon-greedy and the proposed method
or any other analysis.
-  Also, the author mentions that the propose variant works well in Asterix and Freeway(in sec.5). However, I wonder 
that what this might imply. (better for games that need more exploration? It has to be confirmed by visualizing the agent)

# non-official source code
- Tensorflow for [NoisyNet-DQN](https://github.com/andrewliao11/NoisyNet-DQN)
- Pytorch for [NoisyNet-A3C(LSTM)](https://github.com/Kaixhin/NoisyNet-A3C)
