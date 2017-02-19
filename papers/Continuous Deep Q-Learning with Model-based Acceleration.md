# Continuous Deep Q-Learning with Model-based Acceleration

Previous work solving model-free **continuous** control mainly falls inot two group: policy search based method, actor-critic algorithms(intergrate the value function), e.g DDPG, Dyna-Q. 

The difficulty of using Q learning in continuous control is ```argmax Q(s,a)```. This work derive **NAF**, a variant of Q function. Besides NAF, and proposed **imageination rollout** to combine model-based and model-free method.

The author decomposed the Q function into Value function and Advantage function, and advantage funciton is parameterized as a quadratic funciton. (the reason why it works still surprise me, though)

Secondly, the author propose to incorporate model-based technique to increase the sample efficiency in Q learning. Use iLQG to iterative fit the local model(use the sample from the recent episodes)


## keypoints
- Decompose the Q(s,µ) function as V(s)+A(s,µ), assume the the µ(s|θ) always give the action that maximize the Q(s,µ)
- use simple linear model to iteratively fit the model(envs)
- it's will difficult to use non-linear neural network to learn the model(envs). since neural network is usefule when large amount of data, if the data is non i.i.d. :point_right: 

## note/question
- compared with DDPG: 
	- pros: simpler, converge faster
	- cons: without theoretical proof