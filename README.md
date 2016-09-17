# Deep Reinforcement Learning survey
This paper list is a bit different from others. I'll put some opinion and summary on it. However, to understand the whole paper, you still have to read it by yourself!   
Surely, any pull request or discussion are welcomed!

## Before Jump into Deep Reinforcement Learning
If you're a newbie in deep reinforcement learning, I suggest you to read the blog post and open course first.

## Outline
- [Reinforcement Learning Papers](https://github.com/andrewliao11/Deep-Reinforcement-Learning-Survey/tree/master#reinforcement-learning-papers)
- [Open Source](https://github.com/andrewliao11/Deep-Reinforcement-Learning-Survey/tree/master#open-source)
  - Python users
  - Lua users
- [Courses](https://github.com/andrewliao11/Deep-Reinforcement-Learning-Survey/tree/master#course)
- [Textbook](https://github.com/andrewliao11/Deep-Reinforcement-Learning-Survey/tree/master#textbook)
- [Misc](https://github.com/andrewliao11/Deep-Reinforcement-Learning-Survey/tree/master#misc)

## Reinforcement learning Papers
***Mistakes teach us to clarify what we really want and how we want to live.*** That's the spirit of reinforcement 
learning: learning from the mistakes. Let's be the explorer in reinforcement learning!

- ***Episodic Exploration for Deep Deterministic Policies: An Application to StarCraft Micromanagement Tasks*** [[arXiv 2016]](http://arxiv.org/abs/1609.02993)
  - Nicolas Usunier, Gabriel Synnaeve, Zeming Lin, Soumith Chintala
  - StarCraft task: control of multiple agents, low-level control, partially observable environment :point_right: extremely large state/action space
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

## Suggest Paper
  
## Open Source
### :snake: Python users[Tensorflow, Theano]
  - [OpenAI gym](https://gym.openai.com/)
    - RL **benchmarking** toolkit
    - Provide environment and evaluation metrics
  - [Keras](https://github.com/matthiasplappert/keras-rl)
    - Fully compatible with OpenAI
    - Some algorithms have been implement(e.g DQN, DDQN, DDPG, CDQN)
  - [TensorLayer](https://github.com/zsdonghao/tensorlayer)
    - Built on the top of Google TensorFlow
  - [rllab](https://github.com/rllab/rllab)
    - Fully compatible with OpenAI 
    - Continuous control tasks 
    - Nice to implement new algorothms
    - [Benchmarking Deep Reinforcement Learning for Continuous Control](https://arxiv.org/abs/1604.06778)
  - [KEras](https://github.com/osh/kerlym)
    - Built on keras
    - Fully compatible with OpenAI
    - Host a handful of agent of reinforcement learning agents
    - [Deep Reinforcement Learning Radio Control and Signal Detection with KeRLym, a Gym RL Agent](http://arxiv.org/abs/1605.09221)
  - [Deep Reinforcement Learning in TensorFlow](https://github.com/carpedm20/deep-rl-tensorflow)
    - Implemented by @carpedm20
    - Having some basic reinforcement algorothms

### :flashlight: Lua users[Torch]
  - [rltorch](https://github.com/ludc/rltorch), basic reinforcement learning package
  - [awesome-torch for reinforcement learning](https://github.com/carpedm20/awesome-torch#reinforcement-learning)
    - List of open sources for rerinforcement learning 
  - [torch-twrl](https://github.com/twitter/torch-twrl), maintained by twitter
    - [Reinforcement Learning for Torch: Introducing torch-twrl](https://blog.twitter.com/2016/reinforcement-learning-for-torch-introducing-torch-twrl)


## Course
  - [CS 294: Deep Reinforcement Learning](http://rll.berkeley.edu/deeprlcourse/#related-materials)
      - Instructors: John Schulman, Pieter Abbeel
  - [UC Berkeley CS188 Intro to AI](http://ai.berkeley.edu/home.html)
      - [2013 Spring video](https://www.youtube.com/user/CS188Spring2013) on youtube   
  - [Advanced Topics: RL](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html)
      - Instructors: David Silver
  - [Deep learning videoes at Oxford 2015](https://www.youtube.com/playlist?list=PLE6Wd9FR--EfW8dtjAuPoTuPcqmOV53Fu)
      - Instructors: Nando de Freitas
      - lecture 15, 16 are strongly related to reinforcement learning
  
## Textbook
  - [Foundations_of_Machine_Learning](http://www.cs.nyu.edu/~mohri/mlbook/)
      - chapter 14: Reinforcement learning  
  
## Misc
  - [A collection of Deep Learning resources](http://www.jeremydjacksonphd.com/category/deep-learning/)
  - [Deep Reinforcement Learning: Pong from Pixels](http://karpathy.github.io/2016/05/31/rl/), from Andrej Karpathy' blog
      - policy gradient (very clear!)
      - many useful link inside
  - [Guest Post (Part I): Demystifying Deep Reinforcement Learning](https://www.nervanasys.com/demystifying-deep-reinforcement-learning/)
  - [Reinforcement Learning and Control](http://cs229.stanford.edu/notes/cs229-notes12.pdf), lecture from Andrew Ng
      - basic reinforcement learning 
      - continuous state MDPs
  - [DEEP REINFORCEMENT LEARNING](https://deepmind.com/blog), from David Silver, Google DeepMind
      - briefly discuss some work done by deepmind
  - [What are the benefits of actor/critic framework in reinforcement learning?](https://www.quora.com/What-are-the-benefits-of-actor-critic-framework-in-reinforcement-learning)
      - Clearly expain the advantages of actor/critic 
  - [Deep Reinforcement Learning: A Tutorial](https://gym.openai.com/docs/rl)
      - It's good to be a kick-off for newbie in reinforcement learning 
