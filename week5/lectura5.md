# Combining predictions for accurate recommender systems

The authors review several techniques explored for achieving one of the top scores on the Netflix Prize recommendation challenge. 
They compare a baseline of a regularized linear regression to several collaborative filtering methods, including traditional 
boosted decision trees and more recent shallow neural networks. One of the main findings is that blending methods that look incompatible,
as they were designed with radically different inductive biases and data modeling approaches, results in a considerable decrease in RMSE.

Overall, I appreciate the detailed explanation of every method and hyperparameters which led to the best configurations. 
In particular, it is delightful to see an asymptotic analysis for the memory and space requirements posed by each algorithm,
as no matter how accurate a RecSys may be, if it cannot scale up to the data, it is practically useless outside the academic world.
For instance, they acknowledge the usefulness of shallow neural networks, as they are able to predict up to a million ratings in a matter of minutes. 
In contrast, they were memory-limited when testing KNN or KRR, as they managed to train on just 6% of the data before running out of RAM.

I consider the next logical step is to systematically test the applicability of the same methods to other recommendations domains, 
as the paper is focused just on the Netflix dataset. It would be specially insightful to compare the blending weights assigned to the optimal
linear combination in a similar data setting, to check whether the larger weights are assigned to the same methods
and look for data dependent influences.
Similarly, one could test if the best performing (single) methods for the Netflix dataset still are for other settings 
(meaning they are strictly superior)
or their success was pure statistical coincidence.

Another interesting research question is to benchmark the proposed methods against the state-of-the-art, as well as looking for a theoretical
upper bound for the performance on similar datasets to assess how much progress has been made in ten years.