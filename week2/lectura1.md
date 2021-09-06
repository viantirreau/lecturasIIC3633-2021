In the realm of recommender systems, where one can choose between the content filtering and collaborative filtering approaches,
ultimately most of the decisions made in the industry are driven by operative costs and real time availability, 
saving the squeeze of the last thousandths of a point in the benchmarks for competitions and academic research.

Content filtering systems usually require gathering external information to build user o items profiles,
which in turn may need field experts or less UX-friendly use cases. On the other end of the spectrum,
neighbor-based collaborative filtering approaches rely on the community perception of the items. 
They almost always suffer from cold start problems and tend to gravitate towards highly rated content, in detriment of niche users 
which have less neighbors to base a predicted rating on.

Matrix factorization methods constitute the middle ground of the previous techniques. They employ latent factors comparable to what experts 
could gather in content filtering scenarios, but seek to explain most of the variance with just a few dimensions.
In particular, some approximate SVD, while proposing some workarounds to the limitations of singular value decomposition. 
For instance, plain SVD is not defined over missing ratings, so imputing them with some sort of average is a must. 
As a mitigation, stochastic gradient descent is described in FunkSVD, and only uses the known ratings to factor the item and user matrices.

Two interesting methods that caught my attention were ALS and time-dependent systems. The former is called "Alternating Least Squares",
and is a pretty intelligent decomposition of the SVD loss function. When both the user and item variable vectors are free, 
the problem is non-convex, but by (temporarily) fixing one of the two, the remaining free variable converts into the well-known, 
convex least-squares problem. As such, by alternating which variable is fixed and optimizing the other one, minimization is guaranteed. 
Although not as fast as SGD, ALS is known to be easily parallelizable, whereas SGD is bound to be computed sequentially and is hardly distributable.

Time-dependent systems, on the other hand, take into account a dynamic modeling of both the user preferences and biases, as well as item trends,
which translate into time-dependent item biases. This makes recommender systems much more aware of ever-changing preferences and scratches the 
surface of online learning, a topic that deserves much more than a mention.

# Online learning and how it challenges Deep NNs

Online learning is a group of learning tasks whose training data comes as a sequential, you-only-look-once stream, opposed to the regular batch-by-batch
setting used in deep neural networks, which allows the data to be learned throughout several training epochs. 
The main challenge that streaming data poses to these types of networks is that the deepest layers struggle to get sufficient gradient 
from backpropagation in an online fashion, as it does not store the data for further training, and thus the network does not fit the observations properly. 
Usually, most online learning is performed with shallow networks (linear or kernel methods) that optimize a convex loss function.

Sahoo et al. ([2017](https://arxiv.org/pdf/1711.03705.pdf)) propose a novel framework for online deep learning to exploit the expressiveness in deep
networks for learning arbitrary functions. They present the so-called Hedge Backpropagation (HBP) to update the network parameters on the fly, 
adapting to concept drift, short-termed trends and fads. 

To achieve an agile system that can learn from streaming data, as well as retaining DNNs expressive power, the HBP method uses an overparameterized
architecture and tries to modulate on or off some of the hidden layers automatically. It uses the first hidden layer to train and predict but if it
is performing badly it starts to use other layers automatically, similar to the way Transformer architectures attend to the data and compute their Query,
Key and Value weights on runtime. In a way, they are also similar to Mixture of Experts models, in the sense that there's a decision to be made
as to what path of the network to use depending on the way the current data looks and how the model is performing.
