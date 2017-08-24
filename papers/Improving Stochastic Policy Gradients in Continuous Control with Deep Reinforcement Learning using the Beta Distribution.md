# Improving Stochastic Policy Gradients in Continuous Control with Deep Reinforcement Learning using the Beta Distribution

accepted in ICML2017

## keypoints
- In continuous control, we oftern resort to [gaussian distribution](https://en.wikipedia.org/wiki/Normal_distribution) to model the continuous action. The benefit of the gaussian 
is that it provides a simple form (mean and sigma) and allow as to reparametrization. 
- However, the gaussian distribution has some drawbacks:
  - it has nonzero probability for any action values (introduce bias if we clip the action values due to the controller limitation)
  - Using gaussian distribution, the variance of the policy gradient estimator is inverse to the \sigma^2. (as the gaussian distribution gets more deterministic the variance become higher and higher)
- [Beta distribution](https://en.wikipedia.org/wiki/Beta_distribution)(beta-dist) comes to rescue:
  - also provide simeple form (\alpha, and \beta)
  - naturally has a **bounded** probability distribution
  - see fig.4 for the relation between beta-dist and log(beta-dist)

## notes
- one of my favorite recent paper (I really like it)
- well-written, and easily to understand their motivation
- Tackles a foundametal question, which serves as convention (using gaussian distribution as policy)
- looks easy for implementation
