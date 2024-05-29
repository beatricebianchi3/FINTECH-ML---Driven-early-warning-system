# FINTECH: ML-Driven Early Warning System
This repository contains the code for a fintech project aimed at developping an **Early Warning System** for market anomaly detection, such as market crashes.

Indeed, one of the main concerns for investors is the market's tendency to crash, since it can lead to significant financial losses. Hence, being able to detect such crashes early on provides several key benefits:
* **Risk management**: EWS help investors and fund managers to take preemptive actions, such as diversifying portfolios, selling off risky assets, or hedging against potential losses;
* **Fraud detection**: Market anomalies can indicate fraudulent activities or market manipulation. Early detection can prevent significant financial crimes and protect the integrity of the market; 
* **Enhance market and operational efficiency**: Early detection of anomalies contributes to market efficiency by providing timely information, leading to better resource allocation and more strategic decision-making;
* **Customer trust**: EWS can boost investors' confidence by safeguarding their financial assets and personal information.

In this project, an EWS is built after a detailed analysis of the strengths and weaknesses of various machine learning classification methods, namely Logistic Regression, Decision Tree, Random Forest, and Support Vector Machine.\
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

## Ensemble Model Development
To enhance model metrics, we developed an ensemble model by combining the best-performing models for each of the four buckets. Each model was trained using the training set and fitted on the validation set. The results from these models served as covariates in a final Logistic Regression model, which was then tested on the test set to determine its effectiveness in detecting market anomalies.

The use of Logistic Regression as the final model also provides us with the ability to understand the influence of different feature groups on our target variable, offering deeper insights into the factors driving market anomalies.

# Repository Structure
- LogisticRegression.ipynb: This notebook contains the implementation and evaluation of a Logistic Regression model for market anomaly detection.
- DecisionTree.ipynb: This notebook details the use of a Decision Tree classifier to identify market crashes.
- SVM.ipynb: This notebook demonstrates the use of a Support Vector Machine (SVM) for classifying market crashes.
- EnsembleModel.ipynb: This notebook consolidates the findings from the previous models, comparing their performance and selecting the best method for market anomaly detection.

# How to Use
- Clone the repository to your local machine.
- Navigate to the directory and open the Jupyter notebooks in your preferred environment.
- Run the notebooks in the sequence provided to replicate the experiments and view the results.
- The final model selection notebook (EnsembleModel.ipynb) will guide you through the process of selecting the most effective model based on our experiments.
