## Comparison of Base Clustering Models

We compared three baseline clustering methods on the UNSW-NB15 network traffic dataset: K-Prototypes, K-Means, and K-Modes. Each model captures a different view of the data because the dataset contains both numerical and categorical features.

### K-Prototypes
K-Prototypes is the most natural baseline for this dataset because it can handle both numerical and categorical features together. In our results, however, most clusters remained fairly mixed. Four of the five clusters were still majority Normal, while one large cluster became more attack-heavy and was dominated by Generic traffic. This suggests that K-Prototypes does capture broad structure in the mixed dataset, but it does not cleanly separate the attack categories under the current off-the-shelf implementation.

### K-Means
K-Means only uses numerical features, so it focuses on behavioral intensity patterns such as rate, load, packet counts, bytes, and timing-related variables. Out of the three baseline methods, K-Means produced the clearest separation. It isolated a strongly Generic-heavy cluster, a strongly Exploit-heavy cluster, and additional clusters that were more normal-heavy. Its PCA visualization also showed the clearest continuous geometric structure, suggesting that many attack patterns differ meaningfully in their numerical behavior.

### K-Modes
K-Modes only uses categorical features, specifically protocol, service, and state. As a result, it groups traffic by connection-type signatures rather than by behavioral magnitude. The results still showed meaningful structure, including a strongly Generic-heavy cluster and a strongly Normal-heavy cluster, but several clusters remained mixed. Its PCA projection looked more discrete and island-like, which is expected because the visualization is based on one-hot encoded categorical data rather than continuous numerical space.

### Overall Comparison
Overall, K-Means produced the strongest empirical separation in our current results, especially for Generic and Exploit-heavy traffic. K-Modes was still useful, but it was limited by only seeing categorical connection identity features. K-Prototypes was the most conceptually appropriate for the mixed dataset, yet it still produced broad and overlapping clusters. Together, these results suggest that simple clustering methods can reveal useful structure in network traffic, but they struggle to fully capture the complexity of the data.

## Why the Base Models Struggle

These baseline models struggle for different reasons. K-Means discards categorical features, K-Modes discards numerical behavior, and K-Prototypes, while more flexible, still relies on relatively simple prototype-based cluster formation. Real network traffic is noisy, overlapping, and nonlinear, and many malicious behaviors resemble normal traffic in some features while differing only in subtle feature combinations.

## Why We Move to a Neural Network

Because of these limitations, we move to a neural network as a stronger next step. The neural network can combine scaled numerical features with encoded categorical features and learn a more expressive internal representation of the data. This allows the model to capture nonlinear interactions and more complex patterns than the baseline clustering methods. In other words, the clustering models help us explore the structure of the traffic, while the neural network helps us learn features that are better suited for separating attack behavior from normal behavior.