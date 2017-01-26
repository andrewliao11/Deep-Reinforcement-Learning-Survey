# Policy Distillation

The authors borrows the concept in model compression into reinforcement learning. The concept is quite simple: use a well-trained agent to teach other random initialized agent. View teacher's transitions as a large an i.i.d. dataset and supervised train the random agent. Instead of calculating loss with maximum likelihood between teacher's action and student's action, it minimize the **Kullback-Leibler divergence (KL) with temperature ⲧ**.   
Multi-task policy distillation: use many experts as many i.i.d. dataset to train an general agent. From table2, the experiment show it can achieve geometric mean at 89%

## keypoints
- distillation method transfer more information from teacher to student.
- temperature of the softmax allows more of the secondary knowledge to be transferred to the student.

## compare
- imitation learning: given **few** teacher's trajectories and learn the policy. Here, all the training trajectories is provieded by teachers. :sweat: a patient teacher

## notes
- high temperature softmax :point_right: become more equally distributed, and vice versa
