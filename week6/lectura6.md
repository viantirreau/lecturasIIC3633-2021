# Deep Learning based Recommender Systems: a survey and new perspectives

Link: https://arxiv.org/pdf/1707.07435.pdf
Year: 2017

The survey highlights the expressive power that neural networks have over more traditional methods, such as matrix factorization or factorization machines, which, after all, are linear models. As it has been shown that a multilayer perceptron can be used as a universal function approximator [1], it is unsurprising that the non-linearities give neural methods an advantage at modeling complex user-item and multi-modal relationships over traditional methods.

One architecture that I found interesting is "Wide and Deep Networks". These are able to strike a balance between memorization and generalization, thus supporting an accurate but diverse recommendation, and have proven useful in Google Play application recommendation. Another remarkable idea is the AutoEncoder family, which works by compressing the input into a bottleneck, low-dimensional latent representation, to then try to reconstruct the original signal, even  handling artificial noise coming from several distributions. 

As a side note, it caught my attention that several typos and grammatical slips were present in the article, suggesting that even more proofreading was needed, specially after seven submissions to arXiv.

Coming back to the topic, Deep Learning has proven so successful in recommender systems that most recent conference papers rely on existing or introduce new DL techniques. One area of personal interest is human resources, which happens to have a specialized "RecSys in HR" A* conference. This week, a paper will be presented in RecSys in HR on the subject of intelligent job-offer to candidate matching via content based recommendation [2]. In particular, the authors, who work in a large HR firm called Randstad, train a language model on semantic similarity between the candidates resumes and the job posting texts. They use a large dataset of successful interviews and hirings as positive examples, while using rejections and some random unseen pairs for negatives. They demonstrate this method is far superior to plain TF-IDF features, as most jobs and skills have several synonyms that are not well captured by TF-IDF.

## References

[1] Kidger, P., & Lyons, T. (2020, July). Universal approximation with deep narrow networks. In Conference on learning theory (pp. 2306-2327). PMLR.

[2] Lavi, D., Medentsiy, V., & Graus, D. (2021). conSultantBERT: Fine-tuned Siamese Sentence-BERT for Matching Jobs and Job Seekers. arXiv preprint arXiv:2109.06501.
