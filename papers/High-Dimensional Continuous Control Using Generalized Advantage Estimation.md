# High-Dimensional Continuous Control Using Generalized Advantage Estimation

This paper introduce an extra hyperparameter λ, which compromise two policy-gradient-based reinforcement learning method 
(REINFORCE and TD). 
In REINFORCE, the advantage function is: $A(s_t, a_t) = \sum_{t}^{\inf} r(s_t, a_t) - V(s_t)$. This algorithm is known for high variance 
and bias-free .

In TD, the advantage function is calulated with bootstrapping:  $A(s_t, a_t) = R(s_t, a_t) - V(s_t)$

