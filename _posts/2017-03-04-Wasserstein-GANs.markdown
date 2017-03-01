---
layout: post
title:  "Wasserstein GANs"
date:   2017-03-03 00:01:59 +0530
---

The Wasserstein GAN (WGAN) is an incredibly recent algorithm developed by researchers at Facebook AI Research for Generative Modeling using
Generative Adversarial Networks (GAN).
If you don't know what Generative Models or GANs are all about [here](https://openai.com/blog/generative-models/)
is a great post by OpenAI explaining why Generative Modeling is so crucial to AI and how GANs work. This rather short post is about how
WGANs work without the technical (but beautiful!) details.

Like all other generative models, the goal of WGANs is to learning the probability distribution $$P_{\theta}$$ so that
it approximates the real distribution of data, $$P_{r}$$, as closely as possible. To do this we first need
to find a way measure how far away $$P_{\theta}$$ is from $$P_{r}$$. WGANs uses the Wasserstein-1 to measure
the distance between probability distributions and it is defined as follows

$$
\mathbb{W}(P_{r}, P_{\theta}) = \underset{w \in W}{\text{max}}\mathbb{E}_{x_{real} \sim P_{r}}(f_{w}(x_{real})) -
\mathbb{E}_{x_{fake} \sim P_{\theta}}(f_{w}(x_{fake})) 
$$

Where, $$f_{w}$$ is function with parameters $$w$$. However, $$f_{w}$$  cannot be just any function, it must be
[$$K$$-Lipschitz](https://en.wikipedia.org/wiki/Lipschitz_continuity), thankfully, we can just do just by restricting
$$w$$ within a particular set of possible
values $$W$$. So what's going on up there? The above equation just says that the distance
between the two distribution $$P_{r}$$ and $$P_{\theta}$$ is equal to the maximum over $$w$$ of the difference between the expectation of
$$f_{w}(x_{real})$$ and $$f_{w}(x_{fake})$$. Different values of $$w$$ would give us different values for this difference, we have to find
the $$w_{max}$$ that maximizes it (but is within $$W$$) to find the correct distance between the two distributions.

We generate $$x_{fake}$$ by sampling a random vector of some size $$k$$ from a prior distribution, $$p_{z}$$ (usually gaussian), and passing it through a neural networks,
$$g_{\theta}$$, with paramters $$\theta$$ which can be learnt.$$^{*}$$
Therefore, we get that $$x_{real} = g_{\theta}(z)$$. The function, $$f_{w}$$, too can be modelled as a neural network with parameters $$w$$ such that
$$w \in W$$.

*$$^{*}$$Technical Note: $$g_{\theta}$$ cannot be just any neural network,
it must be one consisting of affine transformations and nonlinearities which are smooth Lipschitz functions (e.g ReLU, Sigmoid, Tanh, elu, softplus).
This means that most standard neural network architectures work just fine.*


# The Algorithm
The algorithm for training the WGAN is given below

*Initial Parameters:* $$w_{0}$$: initial parameters of $$f_{w}$$, $$\theta_{0}$$: initial parameters of P_{\theta}
$$n_{critic}$$: the number of iterations to per generator iteration, $$m$$: batch size, $$\alpha$$: learning rate
 1. > **while** $$\theta$$ has not converged **do**
 2. > > **for** $$t = 0, \dots, n_{critic}$$ **do**
 3. > > > Sample {$$x_{real}^{(i)}$$} $$ \sim P_{real}$$ a batch of real samples
 4. > > > Sample {$$z^{(i)}$$} $$ \sim p(z)$$ a batch of priors
 5. > > > Calculate gradient w.r.t $$w$$:$$\quad g_{w} \leftarrow \nabla_{w} \left[\frac{1}{m}\sum\limits_{i = 1}^{m}f_{w}(x_{real}^{(i)}) - \frac{1}{m}\sum\limits_{i = 1}^{m}f_{w}(g_{\theta}(z^{(i)}))\right]$$
 6. > > > Update $$w$$:$$\quad w \leftarrow w + \alpha \text{RMSProp}(w, g_{w})$$
 7. > > > Clip $$w$$:$$\quad w \leftarrow \text{clip}(w, -c, c) $$
 8. > > **end for**
 9. > > Sample {$$z^{(i)}$$} $$ \sim p(z)$$ a batch of priors
 10. > > Calculate gradient w.r.t $$\theta$$:  $$\quad g_{\theta} \leftarrow \nabla_{\theta} \left[\frac{1}{m}\sum\limits_{i = 1}^{m}f_{w}(x_{real}^{(i)}) - \frac{1}{m}\sum\limits_{i = 1}^{m}f_{w}(g_{\theta}(z^{(i)}))\right]$$
 11. > > Update $$\theta$$:$$\quad \theta \leftarrow \theta - \alpha \text{RMSProp}(\theta, g_{\theta})$$
 12. > **end while**


 
