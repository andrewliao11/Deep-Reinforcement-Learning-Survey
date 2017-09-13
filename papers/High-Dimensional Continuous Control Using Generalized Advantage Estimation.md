# High-Dimensional Continuous Control Using Generalized Advantage Estimation

This paper introduce an extra hyperparameter λ, which compromise two policy-gradient-based reinforcement learning method 
(REINFORCE and TD). 
In REINFORCE, the advantage function is: 

<p align="center"><img src="https://i.imgur.com/nHW6kpj.png" height="30"/></p>

This algorithm is known for high variance and bias-free .

In TD, the advantage function is calulated with bootstrapping:  

<p align="center"><img src="https://i.imgur.com/lCtv0iL.png" height="30"/></p>

This algorithm is known for low variance and introduce bias.

This paper combine these two methods into "Generalized Advantage Estimation".

## method

Assume that 

<p align="center"><img src="https://i.imgur.com/asAzkPd.png" height="250"/></p>

the above \delta_{i} is the k-step estimators of advantage function. The generalized advantage estimator GAE(γ, λ) is defined as the exponentially-weighted average of these k-step estimators:

<p align="center"><img src="https://i.imgur.com/h6XlY0k.png" height="70"/></p>

## keypoints
- Highly compatible with many policy-gradient-based reinforcement learning algorithms


