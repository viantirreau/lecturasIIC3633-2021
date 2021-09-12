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