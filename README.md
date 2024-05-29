# FINTECH: ML-Driven Early Warning System
This repository contains the code for a fintech project aimed at developping an **Early Warning System** for market anomaly detection (e.g. market crashes).
Indeed, one of the main concerns of the investors is the market tendency to crash, since it can lead to significant financial losses. Hence, being able to detect such crashes early on entails a number of important benefits:
* **Risk management**: EWS help investors and fund managers to take preemptive actions, such as diversifying portfolios, selling off risky assets, or hedging against potential losses;
* **Fraud detection**: market anomalies can sometimes be sign of fraudulent activities or market manipulation; so, detecting these early can prevent significant financial crimes and protect the integrity of the market; 
* **Enhance market and operational efficiency**: early detection of anomalies contributes to market efficiency by providing timely information that can lead to better allocation of resources and more rational and strategic decision-making;
* **Customer trust**: EWS can boost investors' confidence by safeguarding their financial assets and personal information.

In this specific case, an EWS is built after a detailed analysis of the strengths and weaknesses of several machine learning classification methods, namely Logistic Regression, Decision Tree, Random Forest, and Support Vector Machine.
You can find the complete implementation of the models mentioned in the respective Jupyter notebooks of the project.

# Methodology

## Feature Engineering and Data Splitting
The features were divided into four buckets based on prior knowledge of the indices (Bonds, Equities, Commodities, Indexes). This initial grouping allowed us to implement an ensemble model in order to mazimize the performances of our model. After this, the data was split into training (60%), validation (20%), and test (20%) sets to ensure robust model evaluation and selection.

## Repository Structure
- LogisticRegression.ipynb: This notebook contains the implementation and evaluation of a Logistic Regression model for market anomaly detection.
- DecisionTree.ipynb: This notebook details the use of a Decision Tree classifier to identify market crashes.
- SVM.ipynb: This notebook demonstrates the use of a Support Vector Machine (SVM) for classifying market crashes.
- EnsembleModel.ipynb: This notebook consolidates the findings from the previous models, comparing their performance and selecting the best method for market anomaly detection.

## Evaluation Metrics
To determine the best model for market anomaly detection, we focused on three key metrics:

- Precision: Measures the accuracy of the positive predictions, indicating the proportion of true crashes among the detected anomalies.
- Recall: Measures the ability to identify all actual crashes, highlighting the model's effectiveness in capturing all relevant anomalies.
- Accuracy: Provides an overall measure of the model's performance by considering both true positives and true negatives.

These metrics were used to ensure that the selected model reduces the false alarms.

## Ensemble Model Development
To enhance model metrics, we developed an ensemble model by combining the best-performing models for each of the four buckets. Each model was trained using the training set and fitted on the validation set. The results from these models served as covariates in a final Logistic Regression model, which was then tested on the test set to determine its effectiveness in detecting market anomalies.

The use of Logistic Regression as the final model also provides us with the ability to understand the influence of different feature groups on our target variable, offering deeper insights into the factors driving market anomalies.

## How to Use
- Clone the repository to your local machine.
- Navigate to the directory and open the Jupyter notebooks in your preferred environment.
- Run the notebooks in the sequence provided to replicate the experiments and view the results.
- The final model selection notebook (EnsembleModel.ipynb) will guide you through the process of selecting the most effective model based on our experiments.
