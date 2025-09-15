# **DA5401 Assignment \#4 – GMM-Based Synthetic Sampling for Imbalanced Data**

## **Student Information**

**Name:** NAVEETHA NITHIANANDAM  
 **Roll Number:** DA25D005

---

## **Project Overview**

This document accompanies my submission for DA5401 Assignment \#4.  
The objective of the assignment is to address class imbalance in fraud detection using Gaussian Mixture Model (GMM)-based synthetic sampling and clustering-based undersampling (CBU).

The assignment involves:

* Performing data exploration and building a baseline Logistic Regression model on the original imbalanced dataset.  
* Applying advanced resampling methods:  
   • GMM-based synthetic oversampling of the minority class.  
   • Clustering-Based Undersampling (CBU) of the majority class, followed by GMM oversampling.  
* Comparing models on imbalance-robust metrics (Precision, Recall, F1-score) for the minority class.  
* Providing a detailed analysis and recommendation on the effectiveness of GMM in fraud detection.

---

## **Tasks Completed**

### **Part A: Data Exploration and Baseline Model**

* Loaded and analyzed the Credit Card Fraud Detection dataset.  
* Examined class distribution (highly imbalanced: 344 frauds vs. 199,020 normal transactions).  
* Built a baseline Logistic Regression model on the imbalanced dataset.  
* Evaluated with Precision, Recall, and F1-score.  
* Highlighted why accuracy is misleading in imbalanced classification.

### **Part B: GMM-Based Resampling**

* Theoretical Foundation:  
   • Explained the difference between GMM-based oversampling and simpler approaches like SMOTE.  
   • Discussed why GMM better captures complex, multimodal structures in minority data.  
* GMM Implementation:  
   • Fitted GMM on minority data only.  
   • Determined the optimal number of components (k \= 10\) using AIC/BIC analysis.  
* Synthetic Data Generation:  
   • Sampled 198,676 new fraud cases from the fitted GMM.  
   • Combined with original fraud cases to create a balanced dataset (≈398k samples total).  
* Rebalancing with CBU:  
   • Applied KMeans clustering to undersample the majority class from 199k to 5,000 representative centroids.  
   • Used GMM oversampling to expand the minority to 5,000.  
   • Created a compact balanced dataset of 10,000 samples.

### **Part C: Model Comparison and Analysis**

* Trained and evaluated three Logistic Regression models:  
  1. Baseline (Imbalanced data)  
  2. Full GMM-balanced (\~398k samples)  
  3. CBU \+ GMM-balanced (10k samples)  
* Created a summary table and bar chart comparing Precision, Recall, and F1-score for the minority class.  
* Analyzed trade-offs: recall vs. precision.

---

## **Results and Findings**

* Baseline Model:  
   Precision: 0.8362 | Recall: 0.6554 | F1: 0.7348  
   High precision but misses \~35% of fraud cases.  
* Full GMM Balanced:  
   Precision: 0.0606 | Recall: 0.8649 | F1: 0.1133  
   Caught most fraud cases (high recall) but with many false alarms.  
* CBU \+ GMM Balanced:  
   Precision: 0.0067 | Recall: 0.8986 | F1: 0.0133  
   Highest recall, but extremely poor precision, almost all fraud predictions are false alarms.

**Key Insight:**

* GMM-based methods greatly improved recall (fraud detection ability).  
* However, this came at the cost of very low precision.  
* The Full GMM-balanced model offered the best compromise between recall and precision.

---

## **Conclusion**

* Effectiveness of GMM:  
   GMM effectively modeled minority class substructures and boosted recall in fraud detection.  
   Outperformed the baseline in identifying fraud but suffered from low precision.

* Trade-offs:  
   • Full GMM: Best option when recall is prioritized (catching fraud at all costs).  
   • CBU \+ GMM: More efficient, but impractically low precision.

* Final Recommendation:  
   For fraud detection (where missing fraud is costlier than investigating false positives), Full GMM-based oversampling is recommended.  
   For real deployment, hybrid approaches (threshold tuning, cost-sensitive learning, or combining GMM with ensembles) should be explored to balance precision and recall.

---

## **Contact**

For any queries regarding this submission, please feel free to contact me.

