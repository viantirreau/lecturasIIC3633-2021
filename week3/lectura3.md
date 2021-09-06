# Evaluating RecSys

One of the most significant online courses I've taken is "Structuring Machine Learning Projects", taught by Andrew Ng. 
Even though it was nowhere near as mathematically intense as other courses in the Deep Learning Specialization, 
it gave a plethora of heuristics and protocols on how to prepare the data, choose an appropriate metric and modify some hyperparameters to achieve the best performance possible. 
Similarly, this paper is a gentle but thorough review of the techniques that experts use when comparing candidate models, both in the lab and in an online, user-facing fashion.

For instance, the paper highlights the difficulty of modeling simulated users and the biases this choice might introduce in the methods being tested against.
 They also explain when it is best to resort to offline evaluation, a controlled user study or a real world, online experiment.

Although this paper might overwhelm the reader at times, due to numerous, diverse and occasionally disconnected topics, 
it certainly constitutes itself as a great source of information to take advice from when building, evaluating and deploying a new recommender system.
