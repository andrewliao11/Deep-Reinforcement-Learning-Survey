# Unsupervised Perceptual Rewards for Imitation LearningPierre Sermanet, Kelvin Xu, Sergey Levine (RSS2017)

## Keypoints
- Given few **human demonstrations** to learn reward function for **robot manipulation** (different embodiment)
- Learn reward function that are dense and discover subgoals in an unsupervised fashion 
- Use **ImageNet** for pretrained model (without any fintuning)
	- advantage of perceptual reward:
	- just like the advantages in computer vision: learn semantic meaning, ignoring unrelated object (backgroud)
-  To avoid overfitting to small amount of demonstration, use only time-independent gaussian to approximate the reward function (one quadratic reward function for each subgoal)
	
	
## Question
- Why the model trained on ImageNet can be that useful for robot manipulation? or it's depends on task? 