# Evaluating RecSys

One of the most significant online courses I've taken is "Structuring Machine Learning Projects", taught by Andrew Ng. 
Even though it was nowhere near as mathematically intense as other courses in the Deep Learning Specialization, 
it gave a plethora of heuristics and protocols on how to prepare the data, choose an appropriate metric and modify some hyperparameters to achieve the best performance possible. 
Similarly, this paper is a gentle but thorough review of the techniques that experts use when comparing candidate models, both in the lab and in an online, user-facing fashion.

For instance, the paper highlights the difficulty of modeling simulated users and the biases this choice might introduce in the methods being tested against.
They also explain when it is best to resort to offline evaluation, a controlled user study or a real world, online experiment.

Although this paper might overwhelm the reader at times, due to numerous, diverse and occasionally disconnected topics, 
it certainly constitutes itself as a great source of information to take advice from when building, evaluating and deploying a new recommender system.

# Statistical precipice in evaluation

A very recent paper on evaluation metrics and the importance to treat measurements as random variables was published under the title ["Deep Reinforcement Learning at the Edge of the Statistical Precipice"](https://arxiv.org/abs/2108.13264) (2021). It highlights that the metrics published by highly influential papers in the Reinforcement Learning scene (like DeepMind's AlphaGo and MuZero) hide or poorly report an enormous variability in point-wise measurements. This random nature might be particularly misleading when falsely reporting a new state of the art, which may steer the academic progress away from good methods, and even worse, impact the performance of real-world production algorithms that may be replaced by supposedly better ones.

They acknowledge that large scale experiments become prohibitively expensive to recreate on multiple random seeds to measure the real variance, and suggest to use a metric which averages the data between the first and third quartile, coined "interquartile mean". They show this method is significantly less sensitive to outliers compared to the regular mean, as well as being more sensitive to changes in the lower half of the data than the median (because replacing almost 50% of the smallest observations by zero does not affect the latter). Finally, they conduct an interesting analysis showing the variations the point-wise reported metrics exhibit, hindering reproducibility and ignoring statistical uncertainty. To overcome that, they recommend to use stratified bootstrap confidence intervals.