# TOR Traffic Detection

## Introduction
----------------
The TOR (Onion Router) network provides a safe place for Internet users to exchange data without revealing their identity and obfuscates the traffic which makes it difficult for potential observers or eavesdroppers to trace the user's online activities. While TOR software has enhanced online privacy for users, it has also paved a way for the criminals to engage in illicit activities while remaining anonymous, thereby posing significant challenges for law enforcement agencies in their efforts to trace and apprehend wrongdoers. Thus, classifying TOR traffic from non-TOR traffic is critical to trace the Darknet users. In addition, it can be effective in intrusion detection systems (IDS) and intrusion prevention systems (IPS) which rely on knowledge of normal network behavior to detect and prevent such attacks.

This project addresses the critical issue of **detecting TOR and non-TOR** traffic within network data, aiming to uncover activities within TOR traffic that compromise user protection. Leveraging the [UNB-CIC TOR Network Traffic dataset](https://www.unb.ca/cic/datasets/tor.html), a comprehensive study is conducted to compare the efficacy of Random Forest, Logistic Regression, and Bagged Logistic Regression in classifying TOR and non-TOR traffic (Scenario 1). Further, we use Random Forest, Decision Trees, XGBoost, and voting classifier, which is the ensemble of XGBoost and Random Forest to classify the type of

TOR traffic in classes like audio, browsing, chat, file-transfer, mail, p2p, video, and voip (Scenario 2). The evaluation of models relies on key metrics such as confusion matrix, F1-score, precision, and recall. Experimental findings indicate that all models in Scenario 1 could detect TOR traffic with high performance while Random Forest has the best performance. For Scenario 2 also all models show good results in classifying the type of the traffic although XGBoost model performs the best.