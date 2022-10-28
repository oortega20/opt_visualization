

# Optimizer Visualization

When taking machine learning courses, I was always fascinated with gradient descent algorithms such as SGD.
I always loved the analogy of the ball moving down the hill and how this analogy can be expressed in a mathematically rigorous way using tools such as multi-variable calculus. 
I did this project simply because I like to see these series of algorithms visually. Also, the only thing better than a ball rolling down a hill is many balls rolling down a hill :).

In general, these gradient-based optimization methodologies will iteratively seek to minimize a **loss function** $L$ with respect to weight vector $w$. The update rule used to choose $w$ is in itself a function of gradient of the loss with respect to $w$ 

## Gradient Descent

Given a loss function $L$ with learning-rate $\lambda$ we can describe the optmization procedure for gradient descent as follows:

$$w_{n+1} = w_{n} - \lambda * \nabla_{w}L(w)$$

This tells us that the new loss will be equal to the following:

$$L(w_{n+1}) = L(w_{n} - \lambda * \nabla_{w}L(w))$$

Notice that because the gradient of the loss function with respect to $w$ is the direction of greatest increase of the loss. Having the updated $w$ move in the direction of the negative gradient will make the updated $w$ tend to the direction of greatest decrease. Makes sense if you ask me.

## Gradient Descent with Momentum

Given a loss function $L$ with learning-rate $\lambda$ and momentum parameter $\gamma$ we can define the optimization procedure as follows:

$$v_{t+1} = \gamma * v_{t} + \lambda \nabla_{w}L(w)$$

$$w_{t+1} = w_{t} - v_{t+1}$$

Substituting the expression for $v_{t+1}$ we get the following:
$$= w_{t} - (\gamma * v_{t} + \lambda \nabla_{w}L(w))$$

The value of $\gamma$ is typically between 0 and 1. Also notice that if we set $\gamma$ to 0 we end up with the same equation for gradient descent!

## Gradient Descent with Nesterov Momentum

When performing gradient descent with the nesterov update term, the gradient term is not computed from the current position $w_{t}$ in the parameter space, but instead from a position $w_{\textrm{lookahead}} = w_{t} + \mu v_{t}$. This helps because even if the momentum term points in the wrong direction or overshoots the current step, the gradient can still "correct" in the same update step based on the location of the lookahead term.


Given a loss function $L$ with learning-rate $\lambda$ and momentum parameter $\gamma$ we can define the optimization procedure as follows:

$$v_{t+1} = \gamma * v_{t} + \lambda \nabla_{w}L(w + \gamma v_{t})$$

$$w_{t+1} = w_{t} - v_{t+1}$$

$$w_{t+1} = w_{t} - (\gamma * v_{t} + \lambda \nabla_{w}L(w + \gamma v_{t}))$$

## RMSProp
**Root Mean Squared Propagation** is an extension of gradient descent that uses a decaying average of partial gradients as the adaptation for the step-size of each parameter. 

Given a loss function $L$ with learning-rate $\lambda$ and momentum parameter $\gamma$ we can define the optimization procedure as follows:

$$v_{t} = \gamma v_{t-1} + (1 - \gamma) * \nabla_{w}(L(w))^{2}$$ 

$$\Delta w_{t} = - (\frac{\lambda}{\sqrt{v_{t} + \epsilon}} * \nabla_{w}(L(w)))$$

$$w_{t+1} = w_{t} + \Delta w_{t}$$

Notice how the $v_{t}$ term will scale each corresponding parameter in $w$ according to a exponential moving average of the previous gradients. Here the $\epsilon$ parameter is used to avoid division by 0. 

## Adam

Now that we understand the ideas behind RMSProp and Gradient Descent with momentum, it gives us all we need to understand Adam. Adam or **Adaptive Moment Optimization** is simply the combination of the heuristic approaches to optimization that both algorithms use.

Given a loss function $L$ with learning-rate $\lambda$, $\beta_{1}$, and $\beta_{2}$ we can define the optimization procedure as follows:

$$v_{t} = \beta_{1} v_{t-1} - (1 - \beta_{1}) * \nabla_{w}(L(w))$$ 

$$s_{t} = \beta_{2} * s_{t-1} - (1 - \beta_{2}) * \nabla_{w}(L(w))^{2}$$

$$\Delta w_{t} = - (\lambda \frac{v_{t}}{\sqrt{s_{t} + \epsilon}} * \nabla_{w}(L(w)))$$

$$w_{t+1} = w_{t} + \Delta w_{t}$$

Again notice, how if $\beta_{1} = 1$ the equation reduces to RMSProp! Similarily, if $\beta_{2} = 1$ The formula reduces to Gradient descent with momentum with a new learning rate $\lambda_{\text{new}} = \frac{\lambda}{\sqrt{s_{t} + \epsilon}}$

Enjoy,


Oscar Ortega

![](https://github.com/oortega20/opt_visualization/blob/master/opt.gif)
