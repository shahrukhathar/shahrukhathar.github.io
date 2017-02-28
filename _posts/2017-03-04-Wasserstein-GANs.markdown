---
layout: post
title:  "Wasserstein GANs"
date:   2017-03-03 00:01:59 +0530
---

The Wasserstein GAN (WGAN) is an incredibly recent algorithm developed by researchers at Facebook AI Research for Generative Modeling using
Generative Adversarial Networks (GAN).
If you don't know what Generative Models or GANs are all about [here](https://openai.com/blog/generative-models/)
is a great post by OpenAI explaining why Generative Modeling is so crucial to AI and how GANs work. This rather short post is about how
they work without the technical (but beautiful!) details.

Like all other generative models, the goal of WGANs is to learning the probability distribution $P_{\theta}$ so that
it approximates the real distribution of data, $P_{r}$, as closely as possible. To do this we first need
to find a way measure how far away $P_{\theta}$ is from $P_{r}$. WGANs uses the Wasserstein-1 to measure
the distance between probability distributions and it is defined as follows

$$

\mathbb{W}(P_{r}, P_{\theta}) = \underset{w \in W}{\text{max}}
\mathbb{E}_{x_{real} ~ P_{r}}(f_{w}(x_{real})) - \mathbb{E}_{x_{fake} ~ P_{\theta}}(f_{w}(x_{fake})) 

$$

Where, \(f_{w}\) is function with parameters \(w\). However, $f_{w}$  cannot be just any function, it must be
[$K$-Lipschitz](https://en.wikipedia.org/wiki/Lipschitz_continuity), thankfully, we can just do just by restricting $w$ within a particular set of possible
values $W$. So what's going on up there? The above equation just says that the distance
between the two distribution $P_{r}$ and $P_{\theta}$ is equal to the maximum over $w$ of the difference between the expectation of
$f_{w}(x_{real})$ and $f_{w}(x_{fake})$. Different values of $w$ would give us different values for this difference, we have to find
the $w_{max}$ that maximizes it (but is within $W$) to find the correct distance between the two distributions. 
