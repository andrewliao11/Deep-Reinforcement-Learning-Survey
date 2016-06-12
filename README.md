# Deep Reinforcement Learning survey
This paper list is a bit different from others. I'll put some opinion and summary on it.   
However, to understand the whole paper, you still have to read it by yourself!
Surely, any pull request or discussion are welcomed!
## Papers
  - **Deep Reinforcement Learning with Double Q-learning**, Hado van Hasselt, Arthur Guez, David Silver, [[AAAI 2016]](http://arxiv.org/abs/1509.06461)
      - deal with overestimation of Q-values
      - separate action-select-Q and predict-Q 
  - **Playing Atari with Deep Reinforcement Learning**, Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Alex Graves Ioannis Antonoglou, Daan Wierstra [[NIPS 2013 Deep Learning Workshop]](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf)
  - **Human-level control through deep reinforcement learning**, [[Nature 2015]](http://home.uchicago.edu/~arij/journalclub/papers/2015_Mnih_et_al.pdf)
      - Experience replay
      - Iterative update Q-value
      - [Source code](https://sites.google.com/a/deepmind.com/dqn)
  - **Asynchronous Methods for Deep Reinforcement Learning**, Volodymyr Mnih, Adrià Puigdomènech Badia, Mehdi Mirza, Alex Graves, Timothy P. Lillicrap, Tim Harley, David Silver, Koray Kavukcuoglu, [[ICML 2016]](https://arxiv.org/abs/1602.01783)
      - Implementation from others:  [async-rl](https://github.com/muupan/async-rl)
      - [Asynchronous SGD](https://cxwangyi.wordpress.com/2013/04/09/why-asynchronous-sgd-works-better-than-its-synchronous-counterpart/)
  - **Learning Hand-Eye Coordination for Robotic Grasping with Deep Learning and Large-Scale Data Collection**, Sergey Levine, Peter Pastor, Alex Krizhevsky, Deirdre Quillen, [[arXiv 2016]](http://arxiv.org/abs/1603.02199)
      - [Deep Learning for Robots: Learning from Large-Scale Interaction](https://research.googleblog.com/2016/03/deep-learning-for-robots-learning-from.html)
  - **Active Object Localization with Deep Reinforcement Learning**, Juan C. Caicedo, Svetlana Lazebnik, [[ICCV 2015]](http://arxiv.org/abs/1511.06015)
      - Agent learns to deform a bounding box using simple transformation action   
  - **Dueling Network Architectures for Deep Reinforcement Learning**, Ziyu Wang, Tom Schaul, Matteo Hessel, Hado van Hasselt, Marc Lanctot, Nando de Freitas, [[ICML 2016]](http://arxiv.org/abs/1511.06581)
      - two stream network(state-value and advantage funvtion)
      - Torch blog - [Dueling Deep Q-Networks](http://torch.ch/blog/2016/04/30/dueling_dqn.html)   
  - **Memory-based control with recurrent neural networks**, Nicolas Heess, Jonathan J Hunt, Timothy P Lillicrap, David Silver, [[NIPS 2015 Deep Reinforcement Learning Workshop]](http://arxiv.org/abs/1512.04455)
      - solve partially-observed problem  





## Open Source
  - [OpenAI gym](https://gym.openai.com/), RL benchmarking toolkit

## Course
  - [CS 294: Deep Reinforcement Learning](http://rll.berkeley.edu/deeprlcourse/#related-materials), Instructors: John Schulman, Pieter Abbeel
  - [UC Berkeley CS188 Intro to AI](http://ai.berkeley.edu/home.html)
  - [Advanced Topics: RL](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html), Instructors: David Silver
  
## Textbook
  - [Foundations_of_Machine_Learning](http://www.cs.nyu.edu/~mohri/mlbook/)
      - chapter 14: Reinforcement learning  
   
  
## Useful links
  - [A collection of Deep Learning resources](http://www.jeremydjacksonphd.com/category/deep-learning/)
  - [Deep Reinforcement Learning: Pong from Pixels](http://karpathy.github.io/2016/05/31/rl/), from Andrej Karpathy' blog
  - [Guest Post (Part I): Demystifying Deep Reinforcement Learning](https://www.nervanasys.com/demystifying-deep-reinforcement-learning/)
