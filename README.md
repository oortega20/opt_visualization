

# Optimizer Visualization

When taking machine learning courses, I was always fascinated with gradient descent algorithms such as SGD.
I always loved the analogy of the ball moving down the hill and how this analogy can be expressed in a mathematically rigorous way using tools such as multi-variable calculus. 
I did this project simply because I like to see these series of algorithms visually. Also, the only thing better than a ball rolling down a hill is many balls rolling down a hill :).

In general, these gradient-based optimization methodologies will iteratively seek to minimize a loss function $L$ with respect to weight vector $w$. The update rule used to choose $w$ is in itself a function of gradient of the loss with respect to $w$ 

## Gradient Descent

Given a loss function $L$ with learning-rate $\lambda$ we can describe the optmization procedure for gradient descent as follows:

$$w_{n+1} = w_{n} - \lambda * \nabla_{w}$$

This tells us that the new loss will be equal to the following:

$$L(w_{n+1}) = L(w_{n} - \lambda * \nabla_{w})$$

Notice that because the gradient of the loss function with respect to $w$ is the direction of greatest increase of the loss. Having the updated $w$ move in the direction of the negative gradient will make the updated $w$ tend to the direction of greatest decrease. Makes sense if you ask me.

## Gradient Descent with Momentum

## Stochastic Gradient Descent with Nesterov Momentum

## RMSProp

## Adam



Enjoy,


Oscar Ortega

![](https://github.com/oortega20/opt_visualization/blob/master/opt.gif)
