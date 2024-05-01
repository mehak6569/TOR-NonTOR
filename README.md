# TOR Traffic Detection

### Our Contributors 💫
<a href="https://github.com/mehak6569/TOR-NonTOR/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=mehak6569/TOR-NonTOR" />
</a>

*Made with [contrib.rocks](https://contrib.rocks)*


## Introduction
The TOR (Onion Router) network provides a safe place for Internet users to exchange data without revealing their identity and obfuscates the traffic which makes it difficult for potential observers or eavesdroppers to trace the user's online activities. While TOR software has enhanced online privacy for users, it has also paved a way for the criminals to engage in illicit activities while remaining anonymous, thereby posing significant challenges for law enforcement agencies in their efforts to trace and apprehend wrongdoers. Thus, classifying TOR traffic from non-TOR traffic is critical to trace the Darknet users. In addition, it can be effective in intrusion detection systems (IDS) and intrusion prevention systems (IPS) which rely on knowledge of normal network behavior to detect and prevent such attacks.


## Dataset
The [UNB-CIC Tor Network Traffic Dataset](https://www.unb.ca/cic/datasets/tor.html) has been collected by the Information Security Center of Excellence (ISCX) at the University of New Brunswick in Canada in 2016. This dataset was derived from network traffic analysis, employing Wireshark and was subsequently stored in a pcap file. This dataset have been recorded over a two-week timeframe and extracted from diverse network interfaces and devices, including laptops, smartphones, wired and wireless connections, and servers.

The dataset has been divided into two scenarios:-

1. **Scenario 1**: The data has TOR and non-TOR labels to distinguish between TOR and the normal traffic,
a binary classification problem
2. **Scenario 2**: The data has eight categories: AUDIO, BROWSING, CHAT, FILE-TRANSFER, MAIL, P2P, VIDEO, and VOIP labels that are utilized in detecting the type of network traffic.

This dataset has *67835 samples* and *28 features* like Flow duration (length of the connection (seconds)), Flow bytes (number of bytes sent), Flow packets (number of packets sent), Active (seconds in which the flow has been active), Idle (seconds in which the flow has been idle), etc.


## Methodology
This project aims to compare the performances of different Machine Learning models to find the best method for the efficient detection of TOR traffic. In both the scenarios, the training dataset has a high imbalance in the target classes. For example, in case of scenario 1, there are 597904 nonTOR data points and only 8044 TOR data points. This imbalance in the training dataset influences the performance of machine learning algorithms. We use the concept of dataset sampling to remove this bias in the dataset in order to reduce its influence on machine learning algorithms. Therefore, the optimization steps include balancing the dataset, feature extraction, feature selection, and hyperparameter tuning. 

## Results
The Table I shows the performance of different Tor/non-Tor classifiers for the case when the dataset is balanced using SMOTE and the features are selected using correlation-based feature selection. And Table II shows the performance of the classifiers while identifying the type of TOR traffic when the data is balanced using SMOTE and features are selected using the tree-based classifier. Based on the F1-score values, Random Forest Classifier gives the best results for the scenario-1 and XGBoost is the
best model for the scenario-2. Although models such as Logistic Regression, Bagged Logistic Regression, Decision Trees have not provided f1-scores as good as the other models, they have also achieved an F1-score over 90%.

| Classifier  | Precision | Recall | F1 Score |
| :---         |     :---:      |     :---:      |     :---:      |
| Logistic Regression  | 92.79 | 89.95 | 90.85|
| Random Forest | 99.62 | 99.62 | 99.62 |
| Bagged Logistic Regression | 92.75 | 89.76 | 90.70 |


| Classifier  | Precision | Recall | F1 Score |
| :---         |     :---:      |     :---:      |     :---:      |
| Decision Trees  | 98.11 | 98.06 | 98.07|
| Random Forest | 97.47 | 97.43 | 97.44 |
|XGBoost | 98.95 | 98.93 | 98.93 |
|Voting Classifier (Ensemble of Random forest and XGBoost) | 98.83 | 98.81 | 98.81|

## Conclusion
Synthetic Minority Oversampling Technique has given a better performance overall compared to the cases with random undersampling, random oversampling and no data sampling. This indicates that when there is an equal distribution of classes among the examples, the performance of the classifier increases with an increasing number of examples. 
> **Random Forest** has better performance than decision trees, logistic regression in **scenario-1** as a random forest classifier is an ensemble classifier that uses multiple decision tree results to classify a data point. 
-----
> **XGBoost** gave the better results for the **scenario-2** as compared to random forest, decision trees and even the ensemble of XGBoost and random forest.

As can be seen from the results, Random Forest classifier has produced the best performance in classifying the examples in the dataset as TOR or Non-TOR with an F1 score of 99.62% with the SMOTE method and correlation based feature selection for scenario-1. And XGBoost performed better in the scenario-2 with the F1 score of 98.81 followed by the voting classifier with F1 score at 98.93.



