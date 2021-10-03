# Interactive recommender systems: A survey of the state of the art and future research challenges and opportunities


This comprehensive review focuses on five common recommender systems challenges and how they have been mitigated using interactive visualizations.

For the black-box problem in RecSys (1), the authors argue that transparency and justification are essential for the user to gain confidence and trust the system's recommendations. When involvement is low (2), they find that user controllability is a key factor to raise engagement. 

For the lack of diversity (3), they note that recommending in categories instead of lists has been proposed as a method to increase the perceived diversity, even though the underlying system is barely modified. When facing cold-start issues (4), the authors mention popular item recommendation as an effective method to locate interests in a straightforward way.

Finally, for addressing the challenge of contextual information acquisition and representation (5), they highlight that focusing the visualization and design efforts on affective elements or emotions tends to be successful.

Overall, I was delighted to see a tabular summary of all the methods with their objectives, visualization techniques and recommender algorithms, as it can serve as an index to consult when implementing a user-centric RecSys. 

The review is extensive and covers several dimensions for each considered method, including what they evaluate in the corresponding study, what metrics they use, how they collect the user data and what are their main results. 

What strikes me most is the remaining challenges, in particular the lack of methods that tackle the problem of increasing diversity and serendipity through interactive visualizations. Another interesting observation brought to the table by the review is the scarcity of standardized frameworks to evaluate user-centric systems, which is evident after having presented a wide table of different methods and metrics used by each paper. 

The last point makes me question the validity of the results, as one can perfectly cherry-pick a convenient metric on which carefully chosen baselines perform poorly, while the proposed method is far superior. This evidently calls for objective and widespread frameworks to evaluate visual interactive recommender systems.