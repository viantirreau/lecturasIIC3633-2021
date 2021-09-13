# Content-based RecSys

Content-based recommender systems aim to model a similarity function between items, based on structured attributes or unstructured features they have.
A common approach to implement these systems consists of vectorizing the items in a latent fashion, so that they can be compared,
retrieved and ranked according to the user preferences. 

For example, the chapter alludes to TF*IDF as a technique to vectorize text-based content. While this certainly is not the state-of-the-art anymore, 
having been superseded by Transformer-based language models, the concept remains the same: design a process through which similar 
documents (items) are assigned similar vectors, and then use a distance metric, such as cosine or euclidean distance to find new
(hopefully similar and relevant) items given consumed ones.

An interesting challenge arises when trying to optimize for relevance and diversity/novelty at the same time. 
As content-based methods usually have an inductive bias to cluster similar items together, rarely can one system extract relevant and diverse
items by searching in the neighborhood of a known-relevant. This book section highlights Rocchio's algorithm as a way to iteratively
refine user queries by linearly weighting relevant document vectors and subtracting irrelevant ones from the query vector.
Nevertheless, the authors acknowledge that there is no theoretical basis or performance guarantees in the method, leading me to the conclusion that 
better approaches, potentially learnable end-to-end, can be achieved in order to offer a better recommendation experience.

# Introducing Meta-learning

That last thought motivated me to search for some way to further abstract the recommendation pipeline in a learnable way. 
[Meta-Learning for Recommendation with User-Level Adaptive Model Selection](https://arxiv.org/pdf/2001.10378.pdf) [1] is a 2020 paper which tackles
the problem of having many good-enough models that have an acceptable user coverage, but sadly having to choose only one to deploy in production. 
They challenge this apparent paradigm by proposing a meta-learning framework which selects the **best single model for each user** according to some metric.

The proposed framework is particularly well-suited for online recommender systems, which respond to user input and preferences in real time. 
In this regard, it's close to what Rocchio's algorithm tries to solve, as mentioned in the chapter by Pazzani and Billsus. 

The model selection step is designed to be trained end-to-end and uses meta-learning, which can be summarized as "learning to learn". 
A clear advantage of their approach is that it is task- and model-agnostic, meaning it can adapt to any setting. It can be thought of as a wrapper
over several specialized models: it learns to respond to a task (learn to predict user preference) in order to select a recommendation model.
By leveraging SGD over a pre-trained meta-model, the framework is able to rapidly adapt to user changes.

What amazes me the most of this proposal is the change of perspective. From a (single, one-size-fits-all) matrix factorization model, 
which calculates the inner product between the user and item vector, we jump to a whole new level: as a user, now I can opt to have a specialized model
just for me. As a student just entering the field, this is definitely the time to get into user-centric RecSys.

---

### References

1. Mi Luo, Fei Chen, Pengxiang Cheng, Zhenhua Dong, Xiuqiang He, Jiashi Feng, and Zhenguo Li. 2020. MetaSelector: Meta-Learning for Recommendation with User-Level Adaptive Model Selection. In Proceedings of The Web Conference 2020 (WWW ’20), April 20–24, 2020, Taipei, Taiwan. ACM, New York, NY, USA, 7 pages. [https://doi.org/10.1145/3366423.3379999](https://doi.org/10.1145/3366423.3379999)