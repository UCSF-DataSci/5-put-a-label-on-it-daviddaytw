# Assignment 5: Health Data Classification Results

This file contains your manual interpretations and analysis of the model results from the different parts of the assignment.

## Part 1: Logistic Regression on Imbalanced Data

### Interpretation of Results

In this section, provide your interpretation of the Logistic Regression model's performance on the imbalanced dataset. Consider:

- Which metric performed best and why?
- Which metric performed worst and why?
- How much did the class imbalance affect the results?
- What does the confusion matrix tell you about the model's predictions?

1. Accuracy (91.7%) appears high but is misleading due to the class imbalance, as the model heavily favors the majority class (true negatives).
2. Recall (30.1%) is the lowest, indicating that the model misses most of the actual positive cases (false negatives).
3. The class imbalance significantly distorted model performance. The model is biased toward predicting the negative class, as seen in the confusion matrix where it correctly identifies 1301 true negatives but only 43 true positives, while missing 100 positive cases.
4. The confusion matrix shows the model is effective at predicting the negative class but struggles to identify positive cases, which is common when one class dominates the dataset. This results in poor recall and limits the model's usefulness in applications where identifying the positive class is critical.


## Part 2: Tree-Based Models with Time Series Features

### Comparison of Random Forest and XGBoost

In this section, compare the performance of the Random Forest and XGBoost models:

- Which model performed better according to AUC score?
- Why might one model outperform the other on this dataset?
- How did the addition of time-series features (rolling mean and standard deviation) affect model performance?

1. XGBoost outperformed Random Forest with a near-perfect AUC of 0.997, indicating superior discrimination between classes.
2. XGBoost likely outperforms due to its advanced regularization, boosting approach, and ability to capture complex feature interactions. It also handles imbalanced data better through optimized tree construction and weight adjustment.
3. The inclusion of rolling mean and standard deviation as features likely contributed to performance improvement for both models. These features add temporal context and capture trends or fluctuations, which are especially valuable in health-related time-series data.

## Part 3: Logistic Regression with Balanced Data

### Improvement Analysis

In this section, analyze the improvements gained by addressing class imbalance:

- Which metrics showed the most significant improvement?
- Which metrics showed the least improvement?
- Why might some metrics improve more than others?
- What does this tell you about the importance of addressing class imbalance?

1. Recall increased dramatically from 0.301 to 0.825, showing that the model became far more capable of detecting positive cases after balancing the dataset.
2. Precision decreased from 0.662 to 0.274, reflecting a higher false positive rate. This trade-off is expected when increasing sensitivity (recall).
3. By balancing the data, the model is no longer biased toward the majority class, resulting in better recall. However, with more positive predictions, it also misclassifies more negatives as positives, reducing precision.
4. These results underscore the importance of addressing class imbalance. While precision may decline, improving recall and AUC leads to a more balanced and useful model, especially in health applications where failing to detect positive cases can have serious consequences.

## Overall Conclusions

Summarize your key findings from all three parts of the assignment:

- What were the most important factors affecting model performance?
    1. Class imbalance severely affects model performance, especially recall.
    2. Accuracy alone is not a reliable metric in imbalanced classification tasks.
    3. Addressing class imbalance significantly improves recall and overall model fairness.
    4. Time series features greatly enhance the performance of tree-based models, especially when using powerful algorithms like XGBoost.
- Which techniques provided the most significant improvements?
    1. Balancing the dataset had the most substantial impact on logistic regression, improving recall and AUC.
    2. Incorporating time series features and using XGBoost delivered the best overall performance (AUC = 0.997).
- What would you recommend for future modeling of this dataset?
    1. Always assess multiple metrics beyond accuracy when dealing with imbalanced datasets.
    2. Apply balancing techniques (e.g., resampling, class weighting) during model training.
    3. Use advanced models like XGBoost, especially when temporal patterns are relevant.
    4. Continue exploring additional time-series features and model ensembles to further boost performance
