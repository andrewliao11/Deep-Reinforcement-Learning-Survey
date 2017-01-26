# Reinforcement learning Papers
***Mistakes teach us to clarify what we really want and how we want to live.*** That's the spirit of reinforcement 
learning: learning from the mistakes. Let's be the explorer in reinforcement learning!	


- ***Gradient Estimation Using Stochastic Computation Graphs*** [[NIPS 2015]](https://arxiv.org/abs/1506.05254)
	- John Schulman, Nicolas Heess, Theophane Weber, Pieter Abbeel
- ***Maximum Entropy Inverse Reinforcement Learning*** [[AAAI 2008]](https://www.cs.uic.edu/pub/Ziebart/Publications/maxentirl-bziebart.pdf)
	- Brian D. Ziebart, Andrew Maas, J. Andrew Bagnell, and Anind K. Dey
	- Close to the real case :point_right: the suboptimal case, optimal case can't cover all the state space, and alleviate the reward function ambiguity
	- basic concept: plans with equivalent rewards have equal probabilities, and plans with higher rewards are exponentially more preferred.
- ***Reinforcement Learning with Unsupervised Auxiliary Tasks*** [[arXiv 2016]](https://128.84.21.199/abs/1611.05397)
	- Max Jaderberg, Volodymyr Mnih, Wojciech Marian Czarnecki, Tom Schaul, Joel Z Leibo, David Silver, Koray Kavukcuoglu
	- Introduce an agent that also maximises many other **pseudo-reward** functions simultaneously by reinforcement learning
	- The advantage of auxiliary tasks: in many environment the extrinsic reward is very sparse, which make the feature extractor hard to learn at the beginning. Giving some pseudo reward makes the learner know how to interpret the image at the initial stage.
	- They proposes two main auxiliary task: Pixel changes, Network features.
		- Pixel changes: maximally changing the pixels in each cell of an n*n non-overlapping grid placed over the input image :point_right: make the learner knows to move faster or avoid stopping (I guess)
		- Network features: maximally activating each of the units in a specific hidden layer :point_right: to fully use the hidden units
	- Section 4.1 "Unsupervised Reinforcement Learning" discuss why not use the pixel reconstruction loss
- ***Apprenticeship Learning via Inverse Reinforcement Learning*** [[ICML 2004]](http://dl.acm.org/citation.cfm?id=1015430)
	- Pieter Abbeel, Andrew Y. Ng
	- The first time when apprenticeship is proposed
	- Most of these methods try to directly mimic the demonstrator by applying a **supervised learning** algorithm to learn a direct mapping from the states to the actions. :point_right: only suitable for the case that the taskis to mimic the expert’s trajectory
	- Reward function, rather than the policy or the value function, is the most succinct, robust, and transferable definition of the task,
	- Basic concept: use the inverse reinforcement learning to recover the reward function from the expert and use the that reward function to find the optimal policy.
	- Actually, Apprenticeship Learning doesn't need to find the correct reward function. Instead, it use the predicted reward function to find the policy that is similar to expert.
	- From the experiments, the apprenticeship learning need less sample trajectory than action mimic.
- ***Algorithms for Inverse Reinforcement Learning*** [[ICML 2000]](http://www.andrewng.org/portfolio/algorithms-for-inverse-reinforcement-learning/)
	- Andrew Y. Ng, Stuart Russell
	- In examing animal and human behavior we must consider the reward function as an unknown to be ascertained through empirical investigation.
	- Recover the expert's reward function and this to generate desired behavior
	- Use the eq.4 (see the derivation in the paper, which is quite clear)
	- Avoid reward function ambiguity by adding margin λ|R|
	- Use feature representation for the reward function
		- Since the reward function is assumed to be the linear combination of features, this implies that **if two policy with similar accumulated feature expectation, the accumulated reward is similar**
	- Experiment part shows IRL is soluble at least in **moderate** discrete, continuous space
	- Reference: [Inverse Reinforcement Learning](https://people.eecs.berkeley.edu/~pabbeel/cs287-fa12/slides/inverseRL.pdf), by Pieter Abbeel.
- ***Deep Reinforcement Learning with a Natural Language Action Space*** [[ACL 2016]](Deep Reinforcement Learning with a Natural Language Action Space)
	- Ji He, Jianshu Chen, Xiaodong He, Jianfeng Gao, Lihong Li, Li Deng, Mari Ostendorf
	- Task: String of text :point_right: state, several strings of text :point_right: potential actions
	- other
- ***Imitation Learning with Recurrent Neural Networks***[[arXiv 2016]](https://arxiv.org/abs/1607.05241)
	- Khanh Nguyen
	- Aims to unify two sequence prediction network: learning to search(L2S) and recurrent neural network
	- supervised recurrent neural entwork makes an independent prediction at each time step, which suffers seriously from **compounding errors** since the input observations correlate and thus violate the identically independent distributed assumption required by any supervised approach. 
	-  L2S algorithms reduce a sequential prediction problem to learning a policy to traverse in a search space with minimum cost. It garantees that compounding errors grow linearly with trajectory lengths.
	-  Map the RNN components to L2S (take sequence2sequence for example): 
		-  hidden representation :point_right: St
		-  decoded word :point_right: At 
		-  encoded word :point_right: Xt (new information for the environment)
		-  The non-linear gates in RNN are served to be the trainsition function
- ***Language Understanding for Text-based Games Using Deep Reinforcement Learning*** [[EMNLP 2015]](https://arxiv.org/abs/1506.08941)
	- Karthik Narasimhan, Tejas Kulkarni, Regina Barzilay
	- Use natural language as state representation, and fixed action space (not output natural language in free-form :point_right: major restriction)
		- :star: challenging part: the environment is not directly observable
		- The task includes text interpretation and learning strategy build on the text interpretation 
	- 	Use LSTM to interpret the state(in natural langiage form), and use DQN to select to corresponding action
	-  Basically follow the [deepmind paper](http://www.nature.com/nature/journal/v518/n7540/full/nature14236.html). With experience replay and mini-batch update
	-  Using tSNE for the represnetation analysis is really cool (fig. 5)
- :star: ***High-Dimensional Continuous Control Using Generalized Advantage Estimation*** [[ICLR 2016]](https://arxiv.org/abs/1506.02438)
	- John Schulman, Philipp Moritz, Sergey Levine, Michael Jordan, Pieter Abbeel
	- In extremely high dimensional task(like continuous control in 3D environment), stability is a key point.
	- Propose an effective variance reduction scheme for policy gradients, which called generalized advantage estimation (GAE)
	-  Motivation of GAE: Supposed we have fixed length of steps, from eq.15,  we know that the bias of each advantage function is **k-dependent**. So, as k increases, the biased term becomes more ignorable, while the variance increases and vice versa. (if you found this concept is abstract, think of MC is unbiased but with high variance, while TD is biased, but with los variance)
	-  ***λ*** is a new concept included in this paper. 
		-  If λ = 0 (like eq.17), then we have low variance, and is biased
		-  If λ = 1 (like eq.18), then we have high variance, and is unbased
- :star: ***Recurrent Models of Visual Attention*** [[NIPS 2014]](https://arxiv.org/abs/1406.6247) 
  - Volodymyr Mnih, Nicolas Heess, Alex Graves, Koray Kavukcuoglu
  - Motivation: computationally expensive when dealing with large image. Many attention methods computation cost is propotional to the image size.
  - Use the action control to attend part of image (define a Gaussian, and use treat the location(mean of Gaussian) as action)
  - Can be viewed as POMDP (partially observation markov decision process)
  - The location network is a 2D-Gaussian distribution
  - Action is stochastically drawn from the distribution of location network
  - Reward can be task-dependent (this paper is used in classification)
  - Use the policy gradient to optimize
- ***Deterministic Policy Gradient Algorithms*** [[ICML 2014]](http://jmlr.org/proceedings/papers/v32/silver14.pdf)
  - D. Silver, G. Lever, N. Heess, T. Degris, D. Wierstra, M. Riedmiller
  - The deterministic policy gradient is just a special case for stochastic policy gradient
  - **Problem of stochastic policy gradient**: as the policy become more and more deterministic, the variance of the policy gradient become larger an larger. Finally, become two delta function :point_right: end up computing the gradient of Q 
  - The stochatic policy gradient ends up calculating the gradient of Q(s,a), a is the mean mean of the policy(assume that the policy is a normal distribution)
  - Intuition: update policy in the direction that ***most improve Q***
  - The trade-off of determinisitic policy: exploration :point_right: off-policy deterministic actor-critic (exploration in Q-learning)
  - In continuous action spaces, greedy policy improvement becomes problematic, requiring a global maximisation at
      every step. Instead, a simple and computationally attractive alternative is to move the policy in the direction 
      of the gradient of Q, rather than globally maximising Q
  - David Silver's talk about [deterministic policy gradient](http://techtalks.tv/talks/deterministic-policy-gradient-algorithms/61098/) in ICML :point_right: very clear!
- ***Prioritized Experience Replay*** [[ICML 2016]](http://arxiv.org/abs/1511.05952)
  -  Tom Schaul, John Quan, Ioannis Antonoglou, David Silver
  -  Use prioritized sampling rather than uniformly sampling
  -  Use transition’s TD error δ, which indicates how **"surprising" or "unexpected" the transition is**
  -  Alleviate the loss of diversity with stochastic prioritization, and introduce bias
  -  Stochastic Prioritization: mixture of pure greedy prioritization and uniform random sampling
- ***Deep Reinforcement Learning with Double Q-learning*** [[AAAI 2016]](http://arxiv.org/abs/1509.06461)
  - Hado van Hasselt, Arthur Guez, David Silver 
  - Deal with overestimation of Q-values
  - Separate action-select-Q and predict-Q 
- :star: ***Asynchronous Methods for Deep Reinforcement Learning*** [[ICML 2016]](https://arxiv.org/abs/1602.01783)
  - Volodymyr Mnih, Adrià Puigdomènech Badia, Mehdi Mirza, Alex Graves, Timothy P. Lillicrap, Tim Harley, 
      David Silver, Koray Kavukcuoglu 
  - On-policy updates
  - Implementation from others:  [async-rl](https://github.com/muupan/async-rl)
  - [Asynchronous SGD](https://cxwangyi.wordpress.com/2013/04/09/why-asynchronous-sgd-works-better-than-its-synchronous-counterpart/), 
      explain what "asynchronous" means. 
  - [Tuning Deep Learning Episode 1: DeepMind's A3C in Torch](http://www.allinea.com/blog/201607/tuning-deep-learning-episode-1-deepminds-a3c-torch)
- :star: ***Learning Hand-Eye Coordination for Robotic Grasping with Deep Learning and Large-Scale Data Collection*** 
  [[arXiv 2016]](http://arxiv.org/abs/1603.02199)
  - Sergey Levine, Peter Pastor, Alex Krizhevsky, Deirdre Quillen
  - [Deep Learning for Robots: Learning from Large-Scale Interaction]
      (https://research.googleblog.com/2016/03/deep-learning-for-robots-learning-from.html)
- :star: ***Dueling Network Architectures for Deep Reinforcement Learning*** [[ICML 2016]](http://arxiv.org/abs/1511.06581)
  - Ziyu Wang, Tom Schaul, Matteo Hessel, Hado van Hasselt, Marc Lanctot, Nando de Freitas
  - Best Paper in ICML 2016
  - Pose the question: Is conventional CNN suitable for RL tasks?
  - Two stream network(state-value and advantage funvtion)
  - Focusing on innovating a neural network architecture that is better suited for model-free RL
  - Torch blog - [Dueling Deep Q-Networks](http://torch.ch/blog/2016/04/30/dueling_dqn.html)   
- ***Control of Memory, Active Perception, and Action in Minecraft*** [[arXiv 2016]](https://arxiv.org/abs/1605.09128)
  - Junhyuk Oh, Valliappa Chockalingam, Satinder Singh, Honglak Lee
  - Solving problem concerning to partial observability
  - Propose mincraft task
  - Memory Q-Network (MQN), Recurrent Memory Q-Network (RMQN), and Feedback Recurrent Memory Q-Network (FRMQN)
- :star: ***Continuous Control With Deep Reinforcement Learning*** [[ICLR 2016]](http://arxiv.org/abs/1509.02971)
  - Timothy P. Lillicrap, Jonathan J. Hunt, Alexander Pritzel, Nicolas Heess, Tom Erez, Yuval Tassa, David Silver,
     Daan Wierstra
  - Solves the continuous control task, and avoids the curse of **dimension**
  - **Deep** version of DPG(deterministic policy gradient)
  - When going deep, some issues will happens. It's unstable to use the non-linear function to approxiamate 
  - The different components of the observation may have different physical units and the ranges may vary 
      across environments. => solve by batch normalization
  - For exploration, adding the noise to the actor policy: µ0(st) = µ(st|θt µ) + N
- ***Active Object Localization with Deep Reinforcement Learning*** [[ICCV 2015]](http://arxiv.org/abs/1511.06015)
  - Juan C. Caicedo, Svetlana Lazebnik
  - Agent learns to deform a bounding box using simple transformation action(map the object detection task to RL)   
  - Ideas similar to [G-CNN: an Iterative Grid Based Object Detector](http://arxiv.org/abs/1512.07729)
- ***Memory-based control with recurrent neural networks*** [[NIPS 2015 Deep Reinforcement Learning Workshop]]
  (http://arxiv.org/abs/1512.04455)
  - Nicolas Heess, Jonathan J Hunt, Timothy P Lillicrap, David Silver
  - Use RNN to solve partially-observed problem  
- ***Playing Atari with Deep Reinforcement Learning*** [[NIPS 2013 Deep Learning Workshop]](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf)
  - Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Alex Graves Ioannis Antonoglou, Daan Wierstra  
  
 # Suggest Paper
- ***Maximum Entropy Inverse Reinforcement Learning*** [[AAAI 2008]](https://www.cs.uic.edu/pub/Ziebart/Publications/maxentirl-bziebart.pdf)