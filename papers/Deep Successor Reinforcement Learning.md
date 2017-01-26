# Deep Successor Reinforcement Learning


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
