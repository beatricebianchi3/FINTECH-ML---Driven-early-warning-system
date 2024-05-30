# FINTECH: ML-Driven Early Warning System
This repository contains the code for a fintech project aimed at developping an **Early Warning System** for market anomaly detection, such as market crashes.

Indeed, one of the main concerns for investors is the market's tendency to crash, since it can lead to significant financial losses. Hence, being able to detect such crashes early on provides several key benefits:
* **Risk management**: EWS help investors and fund managers to take preemptive actions, such as diversifying portfolios, selling off risky assets, or hedging against potential losses;
* **Fraud detection**: Market anomalies can indicate fraudulent activities or market manipulation. Early detection can prevent significant financial crimes and protect the integrity of the market; 
* **Enhance market and operational efficiency**: Early detection of anomalies contributes to market efficiency by providing timely information, leading to better resource allocation and more strategic decision-making;
* **Customer trust**: EWS can boost investors' confidence by safeguarding their financial assets and personal information.

In this project, an EWS is built after a detailed analysis of the strengths and weaknesses of various machine learning classification methods, namely _Logistic Regression_, _Naive Bayes_, _Decision Tree_, _Random Forest_, _kNN_ and _Support Vector Machine_.\
The complete implementation of these models can be found in the project's respective _Jupyter notebooks_.

# Methodology

## Data overview
The dataset, sourced from Bloomberg, consists of 22-year (2000-2021) weekly data on key equity indices, bond indices, short/medium/long term interest rates, exchange rates, commodities, leading indicators (Economic surprise, Baltic Dry Index) and VIX (option implied volatility).

## Data pre-processing
Missing values in the dataset are removed in order to prevent negative impacts on the output quality.\
Next, features are standardized using _StandardScaler()_ to ensure comparability.\
Finally, data is split into training (60%), validation (20%), and test (20%) sets to ensure robust model evaluation and selection.

## Feature Engineering
Given the advantage of having _prior knowledge_ on the features, data has been divided into **4 buckets**: Bonds, Equities, Commodities and Indexes. Each bucket is studied independently, and the optimal methods for each are included in the final **ensemble model** used for predictions.  

This approach is mainly driven by the several **gains** that could derive from it:
* **Tailored analysis**: Since each bucket represents a distinct financial market segment with unique characteristics and behaviors, the model can leverage domain-specific insights that are more relevant to each type of asset;
* **Complexity reduction**: By breaking the dataset into buckets, models can focus on a narrower scope of features, leading to more straightforward patterns and relationships;
* **Robustness**: Ensemble methods aggregate the predictions from multiple models, leading to more robust and reliable outcomes, potentially reducing the impact of any single model’s weaknesses.

## Evaluation Metrics
To determine the best model for market anomaly detection, we focused on 3 key metrics:

* **Recall**: Measures the ability to identify all actual crashes, highlighting its effectiveness in capturing all relevant anomalies;
* **Precision**: Measures the truthfulness of positive predictions, crucial for minimizing false alarms;
* **Accuracy**: Provides an overall measure of the model's performance by considering both true positives and true negatives.

## Stacking
To enhance our evaluation metrics, we employ a Stacking method, a popular ensemble technique in machine learning. Stacking involves combining multiple weak learners in a parallel manner, and then using a **meta-learner** to integrate their outputs, resulting in improved predictive results.

<div align="center">
  <img src="https://github.com/beatricebianchi3/FINTECH-ML---Driven-early-warning-system/assets/115880372/46cfbd9b-6324-4207-af6b-902a16bfae86" alt="39725Stacking" width="600" height="300">
</div>

In this project, the meta-learner takes the outputs of the best-performing models from each of the four buckets as input and learns how to best combine their strengths to optimize the final prediction performance.

Specifically, **Logistic Regression** is chosen as the meta-learner for several reasons:
* **Probability Scores**: Probability outputs are particularly useful in EWS, since they can be interpreted as the likelihood of a market crash, allowing for a more nuanced decision-making process rather than a binary output;
* **Interpretability**: Logistic Regression's simplicity allows for clear insights into how each feature contributes to the prediction, which is crucial in financial contexts, where decisions need to be explainable to stakeholders;
* **Computational Efficiency**: Logistic regression is computationally efficient, making it feasible to train and update regularly with new data, which is important in dynamic financial markets;
* **Scalability**: It can handle large datasets efficiently, ensuring scalability as the volume of financial data grows over time.

The effectiveness of the Logistic Regression model is assessed using the test set, determining its capability in detecting market anomalies.

# Main Results and Discussion
The primary objective of this project was to develop an effective Early Warning System (EWS) for market anomaly detection using machine learning techniques.\
Therefore, model selection was mainly driven by the maximization of performance metrics such as positive outcomes' **recall**, which assesses the capability of the model to capture the actual market crashes, along with **precision**, which ensures a limited number of false alarms.

## Bucket models
After comparing the validation results of different models on the buckets, the following combination has been adopted:

|                | Model           | Recall (1) | Precision (1) | Accuracy |
|----------------|-----------------|-----------:|--------------:|---------:|
| Bond           | Random Forest   | 0.66       | 0.91          | 0.91     |
| Equity         | kNN             | 0.62       | 0.76          | 0.88     |
| Commodities    | kNN             | 0.64       | 0.81          | 0.89     |
| Indexes        | Random Forest   | 0.64       | 0.94          | 0.91     |

It should be stressed again that the recall and precision reported are referred to the **positive outcomes** (market crashes) only. Instead, the average value of both is around 0.80.

As shown by the table, despite the numerous alternative models and the different nature of the buckets, the best performing ones are always _Random Forest_ and _kNN_.\
This is primarily due to their ability to handle non-linear relationships, capture local patterns, and reduce overfitting. Random Forest’s ensemble approach and feature importance metrics, along with kNN’s sensitivity to local data structures and outliers, make them particularly suited for the complexities of financial market data.\
Their comparative advantages over models like Logistic Regression, Naive Bayes, Decision Tree, and SVM stem from their robustness, flexibility, and effectiveness in capturing intricate patterns in the data.

## Ensemble model results
The Stacking model, using Logistic Regression as the meta-learner, achieved a recall of 0.92, precision of 0.88, and accuracy of 0.90. These results show a significant improvement over the individual models, particularly in terms of recall and precision.


# Repository Structure
- _LogisticRegression.ipynb_: This notebook contains the implementation and evaluation of a Logistic Regression model for market anomaly detection.
- _DecisionTree.ipynb_: This notebook details the use of a Decision Tree classifier to identify market crashes.
- _SVM.ipynb_: This notebook demonstrates the use of a Support Vector Machine (SVM) for classifying market crashes.
- _EnsembleModel.ipynb_: This notebook consolidates the findings from the previous models, comparing their performance and selecting the best method for market anomaly detection.

# How to Use
- Clone the repository to your local machine.
- Navigate to the directory and open the Jupyter notebooks in your preferred environment.
- Run the notebooks in the sequence provided to replicate the experiments and view the results.
- The final model selection notebook (EnsembleModel.ipynb) will guide you through the process of selecting the most effective model based on our experiments.
