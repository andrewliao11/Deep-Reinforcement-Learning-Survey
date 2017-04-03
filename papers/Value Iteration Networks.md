# Value Iteration Networks
The author aims to combine the planning algorithm(value iteration) into a differentiable policy network, making the whole 
model able to train end-to-end. 
```
Value iteration: V_{n+1}(s) = R(s,a) + max{Q_{n}(s,a)}
```

If we see the ```R(s,a)``` as the input of CNN and do convolution on it producing ```Q(s,a)```, then max-pooling on it. the 
whole process is similar to the right hand side of value iteration. If we apply this K times, it simply looks like doing K 
itetaion of value iteration. This method provides us a differential method to embed planning (value iteration) to our NN.

## keypoints
- embed value iteration into NN in a general way
- the advantage of planning: it's invariant to that whether the observation is novel or not
- can't **directly** generalize to continuous domain (perform "high-level" planning on a discrete, coarse grid-world 
representation of the continuous domain)

## notes/question
- the author pay attention on the archietecture of policy network, which makes me think of ***dueling network*** (happy to 
see that there's someone interested in this :smile:)
 
 
## reference
- comments from [@karpathy](https://github.com/karpathy/paper-notes/blob/master/vin.md#misc)
