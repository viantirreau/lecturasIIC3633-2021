# Collaborative Filtering Recommender Systems

Link: https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.130.4520&rep=rep1&type=pdf

Year: 2007

While the information explosion of the early 1990s was overtaking the ability of computers and algorithms to find relevant content between the noise, the systems that took the users' judgement into account proved to be much more accurate and useful than those which relied only on items content features for automated classification and recommendation.

Automated collaborative filtering systems use a database of user profiles and opinions to curate hopefully relevant items for their users, exploiting the information encoded by shared interest communities. The article highlights that the *happy path* for implementing practical CF Recommender Systems includes an abundance of reviews and users, common interests between the users, as well as homogeneous and persistent items, to name a few.

With a gentle historic note on the origin of CF systems, the authors introduce some use-cases and common tools to solve prominent problems in the field. The article also presents a broad overview of some practical concerns for CF Systems, namely cold-starts, the lack of co-ratings and the sheer space requirements of memory-based methods. Some mitigations include dimensionality reduction techniques, albeit with some negative impact to the performance. 

## Amazon: a practical use-case

Interestingly, most of the methods described in the paper are practical only up to the scale of several thousands or few millions of items or users. In contrast, large companies such as [amazon.com](http://amazon.com) have had to develop new algorithms to withstand the scaling issues. Amazon may well be the greatest exponent of item-based CF recommender systems, with hundreds of millions of users and tens of millions of items ([Smith and Linden](https://assets.amazon.science/76/9e/7eac89c14a838746e91dde0a5e9f/two-decades-of-recommender-systems-at-amazon.pdf), 2017; [Smith and Linden](https://cseweb.ucsd.edu//classes/fa17/cse291-b/reading/Amazon-Recommendations.pdf), 2003). They power sub-second recommendations in multiple stages of the e-commerce process, all while avoiding dimensionality reduction or clustering techniques that they show to hurt accuracy. With an intelligent factorization of the expected number of users that buy the product Y given they bought X, Amazon is able to leverage huge offline precomputed interactions to detect "unusually likely" correlations. Specifically, they know "how many X-buyers would have randomly bought Y if the two items were unrelated", and use that as a predictor for effectively popular (i.e. statistically more than random) item pairs.

## Attempting to address CF privacy concerns

A poorly designed rating or implicit feedback loop for use in CF systems can give away users' potentially sensitive information about interests of political, sexual or religious nature. 

A nice example to visualize a non-privacy preserving system, ignoring the *recommendation* part for the moment, is one that aggregates some statistic, for example Fintual's assets under management. If that measurement was real time and one attacker could know when a particular user withdraws all their money, then even without physical access to the compromised user's account, the attacker could deduce how much money it was by looking at the change in the statistic.

As a mitigation, some research lines have suggested adding noise to the datasets in an effort to make user identification or profiling intractable. Nevertheless, the influence on recommendation accuracy is rarely discussed, let alone measured. A [recent paper](https://dl.acm.org/doi/10.1145/2875475.2875483), from Xue Shu and Yuqing Sun (2016), proposes a solution using techniques from differential privacy, based on the [exponential mechanism](https://en.wikipedia.org/wiki/Exponential_mechanism_(differential_privacy)) to protect the users' privacy while also preserving the performance of item- and user-based recommendation methods.

The authors calculate a theoretical error bound for both the probability of breaking the privacy and for the data to be so perturbed as to harm the performance of classical recommendations algorithms. Additionally, they test their privacy-preserving proposal in a Netflix dataset, showing that the performance hit is negligible, and approaches competitive (non-privacy-aware) algorithms as the number of users increases.
