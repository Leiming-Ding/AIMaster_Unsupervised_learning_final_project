## Explore the relationship between students' motivation and their academic performance

When taking a course, students often have their motivation for this course. For example, they may sense that this course can help them prepare for their future careers, or they may feel that taking this course will possibly take up a large portion of their leisure time. This motivation can affect their exam performance and academic performance. This project aims to explore the relationship between students' motivation and their proximal and distal academic performance.

The goal of this project is to utilize supervised and unsupervised learning models to uncover the relationship between students' motivation and their exam1 performance (proximal academic performance) and their final grade (distal academic performance). As this project is developed for the unsupervised learning project, I will explore different options to cluster their motivation and compare the academic performance differences between different clusters. The reason why unsupervised learning models can be used for this project is that students may have different clusters of motivation, such as high in one construct but low in another construct, and people within the same construct may show the same pattern in academic performance. To note, supervised learning models are still used in this project. This project is an exploratory study to see whether using unsupervised models and supervised models can lead to interpretable results.

---

Data used for this project comes from private data and will not be shared. Any identifiable personal information has been removed for the analysis. We used surveys to measure students' motivation at the beginning of the course and then tracked their exam performance from exam 1 to the final exam and their final grade. This dataset includes 14 variables: 12 motivation variables, exam1 score and final score. The motivation variables are:

- **mastery-approach goal** (e.g., focus on learning and understanding), 
- **performance-approach goal** (e.g., focus on competition with others),
- **performance-avoidance goal** (e.g., focus on avoiding showing bad performance),
- **self-efficacy** (e.g., belief in their own abilities to complete the tasks),
- **theory of intelligence** (e.g., beliefs in growth mindset),
- **attainment value** (e.g., value of the course for their identity and competence development),
- **intrinsic values** (e.g., enjoyment or interest for completing the tasks),
- **utility value** (e.g., perceived use of this course),
- **effort cost** (e.g., efforts need to be sacrificed by taking this course),
- **opportunity cost** (e.g., personal sacrifice in time spent with families and friends),
- **psychological cost** (e.g., emotional cost when taking this course),
- **metacognitive self-regulation** (e.g., their tendency to use metacognitive and self-regulated skills).

These motivation variables are in 6-or-7 likert scales. Exam1 score and final score are from 1 to 100. This dataset includes 524 complete cases for the final analysis.

---

Model architecture: I tried different models in this project. First, I tried supervised learning models (linear regression, decision tree, KNN, random forest, XGBoost, support vector machine, and neural network) to use motivation variables to predict the exam1 score and final score, and compare the model performance in terms of RMSE and R^^2. Then, I tried unsupervised learning models (K-means clustering, Gaussian mixture models, and hierarchical clustering) to cluster the motivation variables first and select the best cluster number. After that, I checked whether the clustering of each motivation variable made sense and whether there were significant difference in exam1 score and final score among different clusters. Finally, I used the motivation variables and the generated clustering to predict the exam1 score and final score to see whether there was an improvement in model performance. During the process, (hyper)parameter tuning was included. For example, for the decision tree, I changed the model_max_depth to see the performance. For the unsupervised learning, I plotted elbow plots and silhouette scores to select the best cluster number.

---

- Correlation analysis results: From the results, we can see that self-efficacy positively related to exam1 score (r = 0.10) and effort cost negatively related to exam1 score (r = -0.14). Self-efficacy, attainment value, and the metacognitive self-regulation positively related to final score and effort cost negatively related to final score.
- From the previous results of relationship between motivation and exam1 score, we know that linear regression had the lowest RMSE but neural networks had the highest RMSE. Linear regression also show the highest R^^2. Here linear regression model achieved the best performance.
- Using k-means clustering for motivation variables, three clusters were the most appropriate based on silhouette score. Cluster 0 and cluster 1 are pretty close but they are different from cluter 2 in terms of mastery-approach goals, performance-approach goals, performance-avoidance goals, and self-efficacy. In the following cells, I ran the analysis to see whether these clusters showed differences in exam1 score and final score. The only difference is in final score. Cluster 0 had statistically significant lower final score than cluster 1. For me, this result did not make sense as cluster 0 had higher values and lower costs about the course than cluster 1, which might produce better results in cluster 0.
- Using GMM clustering, From the results, 3 clusters seemed to be the most appropriate based on the silhouette score. The plot is roughly like the plot produced by k-means clustering. There were no differences in terms of exam1 score and final score among different clusters.
- Using hierarchical clustering, From the results, 4 clusters seemed to be the most appropriate based on silhouette score. Cluster 0 are different from cluster 2 in terms of mastery-approach goal, performance-approach goal, performance-avoidance goal, and self-efficacy. Cluster 0 are different from cluster 1 and cluster 3 in terms of effort cost, opportunity cost, and psychological costs. There were no differences in terms of exam1 score and final score among different clusters.
---

Learning and takeaways: (1) For supervised learning, linear regression and decision trees are the simple models with high interpretability. Random forest, XGBoost, SVM, and neural models are becoming more complex but with low interpretability. In this analysis, I tried different models to predict the exam1 score and final score, simpler models, such as linear regression and decision trees, actually performed a better performance with lower RMSE and higher R^^2; (2) in psychology, due to the data generation because evenly distributed items, there is less nonlinear relationship. Maybe this is one reason why using simpler models works; (3) for unsupervised learning, I tried k-means clustering, GMM clustering, and hierarchical clustering. The number of clusters is chosen by the analysers. Although the number of clusters based on values of each variable theoretically make sense, there are no differences detected among different clusters.



