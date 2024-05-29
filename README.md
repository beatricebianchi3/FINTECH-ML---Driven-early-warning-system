# FINTECH-ML-Driven-early-warning-system
This repository contains the code for a fintech project aimed at identifying market anomalies, specifically market crashes, through various machine learning classification methods. The project is organized into several Jupyter notebooks, each exploring different approaches to anomaly detection.

The goal of this project is to accurately identify market anomalies using machine learning techniques. We have experimented with six different classification methods: Logistic Regression, Decision Tree, Random Forest, and Support Vector Machine (SVM). Each method has been thoroughly evaluated to understand its strengths and weaknesses in the context of market crash detection.

## Feature Engineering and Data Splitting
The features were divided into four buckets based on prior knowledge of the indices (Bonds, Equities, Commodities, Indexes). This initial grouping allowed us to implement an ensemble model in order to mazimize the performances of our model. After this, the data was split into training, validation, and test sets to ensure robust model evaluation and selection.

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
