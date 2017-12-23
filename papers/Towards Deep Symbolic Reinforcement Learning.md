# Towards Deep Symbolic Reinforcement Learning

**disclaimers: this paper is a workshop paper in DRL at NIPS2016**

tldr; symbolize the data and do RL for interpretability, and potentially generalizability. 

keywords: symbolic reasoning, reinforcement learning, interpretable NN

People do planning or think complex problems via first make the perception abstract and tackle it. 
This paper explores the how to first symbolize the raw perceptual data and then map 
the symbolic representations into actions.

## Why this matters? and what’s the motivation?

First, they inherit from deep learning the need for very large training sets, 
which entails that they learn very slowly. 
Second, they are brittle in the sense that a trained network that performs well on 
one task often performs very poorly on a new task, 
even if the new task is very similar to the one it was originally trained on. 
Third, they are strictly reactive, meaning that they do not use high-level processes such as planning, causal reasoning, 
or analogical reasoning to fully exploit the statistical regularities present in the training data. 
Fourth, they are opaque. 
It is typically difficult to extract a humanly-comprehensible chain of reasons for the action choice the system makes.

## What does DRL lack? Causal reasoning

To carry out analogical inference at a more abstract level, 
and thereby facilitate the transfer of expertise from one domain to another, 
the narrative structure of the ongoing situation needs to 
be mapped to the causal structure of a set of previously encountered situations. 
As well as maximising the benefit of past experience, 
this enables high-level causal reasoning processes to be deployed in action selection, 
such as planning, lookahead, and off-line exploration (imagination).

## Method
We can view the whole architecture as a model-based RL, 
where the proposed method discovers how to symbolize the data (learn environment dynamics), and learns how to act.

Specifically, the proposed method can be separated into 3 parts: 
low-level symbol generation, representation building, and reinforcement learning.

Low-level symbol generation:
They train a convolutional autoencoder on 5000 randomly generated images. 
The information extracted at this stage consists of 
a symbolic representation of the positions of salient objects in the frame along with their types. (See fig.4)

Representation building: 
They track them across frames in order to observe and learn from their dynamics in the function of Spatial proximity, 
Type transitions, Neighborhood.

Reinforcement learning: tabular Q-learning

## Experiments:
From fig.6, the proposed method works better when the environment is more complex and stochastic.

## Discussion
This paper proposed a naive method the make the proof-of-concept of symbolic RL, 
which I think it’s really good for a workshop paper. 
The author should show how their unsupervised representation can be better 
when the amount of the data become larger and larger. 
Also, the paper doesn’t use the symbolic to do the planning, which they keep emphasize at the beginning.

This paper illustrates the idea in a clear and thought-provoking way, which is the reason I share.
