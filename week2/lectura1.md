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
