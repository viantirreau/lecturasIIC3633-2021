# Deep Learning based Recommender Systems: a survey and new perspectives

Link: https://arxiv.org/pdf/1707.07435.pdf
Year: 2017

The survey highlights the expressive power that neural networks have over more traditional methods, such as matrix factorization or factorization machines, which, after all, are linear models. As it has been shown that a multilayer perceptron can be used as a universal function approximator [1], it is unsurprising that the non-linearities give neural methods an advantage at modeling complex user-item and multi-modal relationships over traditional methods.

One architecture that I found interesting is "Wide and Deep Networks". These are able to strike a balance between memorization and generalization, thus supporting an accurate but diverse recommendation, and have proven useful in Google Play application recommendation. Another remarkable idea is the AutoEncoder family, which works by compressing the input into a bottleneck, low-dimensional latent representation, to then try to reconstruct the original signal, even  handling artificial noise coming from several distributions. 

As a side note, it caught my attention that several typos and grammatical slips were present in the article, suggesting that even more proofreading was needed, specially after seven submissions to arXiv.

## References

[1] Kidger, P., & Lyons, T. (2020, July). Universal approximation with deep narrow networks. In Conference on learning theory (pp. 2306-2327). PMLR.