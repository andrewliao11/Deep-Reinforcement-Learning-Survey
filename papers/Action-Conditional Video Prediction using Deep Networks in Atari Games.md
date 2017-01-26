# Action-Conditional Video Prediction using Deep Networks in Atari Games

- Long-term predictions on Atari games conditional on the action
- Using the predicted frame (more informative) to replace the exploration to improve the model-free controller
- Multiplicative Action-Conditional Transformation: if use ont-hot to represent the action :point_right: each matrix correspond to a transformation matrix
- Learning with Multi-Step Prediction (minimize the k steps accumulated error)
- Section 4.2 is really promising! 
  - replace the real frame by predicted frames
  - use prediction model to help agent explore the state visited least
