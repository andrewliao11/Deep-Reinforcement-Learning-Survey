# Reinforcement learning Papers
***Mistakes teach us to clarify what we really want and how we want to live.*** That's the spirit of reinforcement 
learning: learning from the mistakes. Let's be the explorer in reinforcement learning!	


- ***Deep Reinforcement Learning with a Natural Language Action Space*** [[arXiv 2016]](Deep Reinforcement Learning with a Natural Language Action Space)
	- Ji He, Jianshu Chen, Xiaodong He, Jianfeng Gao, Lihong Li, Li Deng, Mari Ostendorf
	- Task: String of text :point_right: state, several strings of text :point_right: potential actions
	- other
- ***Language Understanding for Text-based Games Using Deep Reinforcement Learning*** [[NMNLP 2015]](https://arxiv.org/abs/1506.08941)
	- Karthik Narasimhan, Tejas Kulkarni, Regina Barzilay
	- Use natural language as state representation, and fixed action space (not output natural language in free-form :point_right: major restriction)
		- :star: challenging part: the environment is not directly observable
		- The task includes text interpretation and learning strategy build on the text interpretation 
	- 	Use LSTM to interpret the state(in natural langiage form), and use DQN to select to corresponding action
	-  Basically follow the [deepmind paper](http://www.nature.com/nature/journal/v518/n7540/full/nature14236.html). With experience replay and mini-batch update
	-  Using tSNE for the represnetation analysis is really cool (fig. 5)
- ***High-Dimensional Continuous Control Using Generalized Advantage Estimation*** [[ICLR 2016]](https://arxiv.org/abs/1506.02438)
	- John Schulman, Philipp Moritz, Sergey Levine, Michael Jordan, Pieter Abbeel
	- In extremely high dimensional task(like continuous control in 3D environment), stability is a key point.
	- Propose an effective variance reduction scheme for policy gradients, which called generalized advantage estimation (GAE)
	-  Motivation of GAE: Supposed we have fixed length of steps, from eq.15,  we know that the bias of each advantage function is **k-dependent**. So, as k increases, the biased term becomes more ignorable, while the variance increases and vice versa. (if you found this concept is abstract, think of MC is unbiased but with high variance, while TD is biased, but with los variance)
	-  ***λ*** is a new concept included in this paper. 
		-  If λ = 0 (like eq.17), then we have low variance, and is biased
		-  If λ = 1 (like eq.18), then we have high variance, and is unbased
- ***Recurrent Models of Visual Attention*** [[NIPS 2014]](https://arxiv.org/abs/1406.6247) 
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
- ***Deep Successor Reinforcement Learning*** [[arXiv 2016]](https://arxiv.org/abs/1606.02396)
  - Tejas D. Kulkarni, Ardavan Saeedi, Simanta Gautam, Samuel J. Gershman
  - Successor Representation(SR): decomposed the value into successor map and reward predictor (the definition of the components in successor representation should be referred to section 3.2)
  - Advantage1: increase the sensitivityof the environment changes, since it records the immediate reward in each 
    state. In DQN, we only record(or predict) the accumulated reward, so the sudden change of reward will be diluted.
    However, the SR mehtod records the reward in each state: R(s), which enable it to be more sensitive to the change
    of environment.
  - Advantage2: able to extract the bottleneck states(subgoals). Since we predict the successor map (the predicted
      visit count), the state with higher visit count is likely to be bottleneck 
  - Section 3.3 is a little tricky. The m_sa represents the **feature of the future occupancy**, so m_sa×W becomes 
      the future accumulated reward (Q-value). The ∅(s)×W is the **immediate reward**. Therefore, 
      m_sa = φ(s) + γE[m_st+1a'] :point_right: eq.6
- ***Deep Reinforcement Learning with Double Q-learning*** [[AAAI 2016]](http://arxiv.org/abs/1509.06461)
  - Hado van Hasselt, Arthur Guez, David Silver 
  - Deal with overestimation of Q-values
  - Separate action-select-Q and predict-Q 
- ***Asynchronous Methods for Deep Reinforcement Learning*** [[ICML 2016]](https://arxiv.org/abs/1602.01783)
  - Volodymyr Mnih, Adrià Puigdomènech Badia, Mehdi Mirza, Alex Graves, Timothy P. Lillicrap, Tim Harley, 
      David Silver, Koray Kavukcuoglu 
  - On-policy updates
  - Implementation from others:  [async-rl](https://github.com/muupan/async-rl)
  - [Asynchronous SGD](https://cxwangyi.wordpress.com/2013/04/09/why-asynchronous-sgd-works-better-than-its-synchronous-counterpart/), 
      explain what "asynchronous" means. 
  - [Tuning Deep Learning Episode 1: DeepMind's A3C in Torch](http://www.allinea.com/blog/201607/tuning-deep-learning-episode-1-deepminds-a3c-torch)
- ***Learning Hand-Eye Coordination for Robotic Grasping with Deep Learning and Large-Scale Data Collection*** 
  [[arXiv 2016]](http://arxiv.org/abs/1603.02199)
  - Sergey Levine, Peter Pastor, Alex Krizhevsky, Deirdre Quillen
  - [Deep Learning for Robots: Learning from Large-Scale Interaction]
      (https://research.googleblog.com/2016/03/deep-learning-for-robots-learning-from.html)
- ***Dueling Network Architectures for Deep Reinforcement Learning*** [[ICML 2016]](http://arxiv.org/abs/1511.06581)
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
- ***Continuous Control With Deep Reinforcement Learning*** [[ICLR 2016]](http://arxiv.org/abs/1509.02971)
  - Timothy P. Lillicrap, Jonathan J. Hunt, Alexander Pritzel, Nicolas Heess, Tom Erez, Yuval Tassa, David Silver,
     Daan Wierstra
  - Solves the continuous control task, and avoids the curse of **dimension**
  - **Deep** version of DPG(deterministic policy gradient)
  - When going deep, some issues will happens. It's unstable to use the non-linear function to approxiamate 
  - The different components of the observation may have different physical units and the ranges may vary 
      across environments. => solve by batch normalization
  - For exploration, adding the noise to the actor policy: µ0(st) = µ(st|θt µ) + N
- ***Mastering the game of Go with deep neural networks and tree search*** [[Nature 2016]](https://vk.com/doc-44016343_437229031?dl=56ce06e325d42fbc72)
  - David Silver, Aja Huang 
  - First stage: supervised learning policy network, including rollout policy and SL policy network(learn the knowledge from human experts)
    -  Rollout policy is used for predicting **fast** but relatively inaccurate decision
    -  SL policy network is used for initialization of RL policy network(improved by policy gradient) 
  - To prevent overfit, auto-generate the sample from self-play(half) and train with the KGS dataset(half)
  - Use Monte Carlo tree search with policy network and value network. To understand the MCTS more, plz refer to [here](https://en.wikipedia.org/wiki/Monte_Carlo_tree_search#Principle_of_operation)
    - Selection: select the most promising action depends on Q+u(P) --> depth L
    - Expansion: after L steps, create a new child
    - Evaluation: evaluated by the mixture of value network and simulated rollout
    - Backup: Calculate and store the Q(s,a), N(s,a), which is used in Selection
- ***Human-level control through deep reinforcement learning***, [[Nature 2015]](http://home.uchicago.edu/~arij/journalclub/papers/2015_Mnih_et_al.pdf)
  - Most optimization algorithms assume that the samples are independently and identically distributed,
      while for reinforcement learning, the data is a sequence of action, which breaks the assumption.
  - Strong correlation btn data => break the assumption of stochastic gradient-based algorithms(re-sampling)
  - Experience replay(off-policy)
  - Iterative update Q-value
  - [Source code [Torch]](https://sites.google.com/a/deepmind.com/dqn)
- ***Active Object Localization with Deep Reinforcement Learning*** [[ICCV 2015]](http://arxiv.org/abs/1511.06015)
  - Juan C. Caicedo, Svetlana Lazebnik
  - Agent learns to deform a bounding box using simple transformation action(map the object detection task to RL)   
  - Ideas similar to [G-CNN: an Iterative Grid Based Object Detector](http://arxiv.org/abs/1512.07729)
- ***Memory-based control with recurrent neural networks*** [[NIPS 2015 Deep Reinforcement Learning Workshop]]
  (http://arxiv.org/abs/1512.04455)
  - Nicolas Heess, Jonathan J Hunt, Timothy P Lillicrap, David Silver
  - Use RNN to solve partially-observed problem  
- ***Action-Conditional Video Prediction using Deep Networks in Atari Games*** [[NIPS 2015]](http://arxiv.org/abs/1507.08750)
  - Junhyuk Oh, Xiaoxiao Guo, Honglak Lee, Richard Lewis, Satinder Singh, [[project page]](https://sites.google.com/a/umich.edu/junhyuk-oh/action-conditional-video-prediction)
  - Long-term predictions on Atari games conditional on the action
  - Using the predicted frame (more informative) to replace the exploration to improve the model-free controller
  - Multiplicative Action-Conditional Transformation: if use ont-hot to represent the action :point_right: each matrix correspond to a transformation matrix
  - Learning with Multi-Step Prediction (minimize the k steps accumulated error)
  - Section 4.2 is really promising! 
    - replace the real frame by predicted frames
    - use prediction model to help agent explore the state visited least
- ***Playing Atari with Deep Reinforcement Learning*** [[NIPS 2013 Deep Learning Workshop]](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf)
  - Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Alex Graves Ioannis Antonoglou, Daan Wierstra  
  
 # Suggest Paper
