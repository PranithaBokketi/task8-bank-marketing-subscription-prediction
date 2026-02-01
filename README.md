Project Overview
This project uses a Decision Tree Classifier to predict whether a bank customer will subscribe to a term deposit based on the UCI Bank Marketing dataset. The focus is on interpretable machine learning using decision rules derived from the tree.

Dataset
Name: Bank Marketing Dataset (UCI Machine Learning Repository)

Link: http://archive.ics.uci.edu/ml/datasets/Bank+Marketing

Target variable:

y – whether the client subscribed to a term deposit (yes / no).
​

Input features include:

Client attributes (age, job, marital, education, default, housing, loan)

Contact details (contact type, month, day, duration)

Campaign and previous contact info (campaign, pdays, previous, poutcome).

Project Structure
Example structure of this repository:

text
.
├── data/
│   └── bank-full.csv
├── notebooks/
│   └── bank_marketing_decision_tree.ipynb
├── images/
│   └── tree_bank_marketing.png
└── README.md
bank_marketing_decision_tree.ipynb: main notebook with EDA, preprocessing, model training, evaluation, and tree visualization.

tree_bank_marketing.png: exported decision tree image.

Methods and Steps
Data Loading & Exploration

Loaded bank-full.csv with ; separator.

Checked basic info, shapes, and target distribution.
​

Data Cleaning & Preprocessing

Standardized categorical text (lowercase, stripped spaces).

Treated "unknown" values, kept them as a separate category.

Split data into features X and target y.

Applied OneHotEncoder to categorical features using ColumnTransformer, passed numeric features unchanged.

Train–Test Split

Used train_test_split with 80% train, 20% test and stratify=y to preserve class balance.

Model Training (Decision Tree)

Model: sklearn.tree.DecisionTreeClassifier with:

criterion='gini'

max_depth=4 to control overfitting

min_samples_split=50

Wrapped preprocessing + model in a Pipeline and fitted on training data.
​

Evaluation

Computed train and test accuracy.

Generated classification report (precision, recall, f1-score) and confusion matrix.

Observed:

Overall accuracy around 90%.

Very high performance on the majority class (no subscription).

Lower recall for the minority class (yes), due to class imbalance.

Tree Visualization

Extracted feature names from the OneHotEncoder.

Plotted the decision tree with plot_tree (feature names, class names, colored nodes).

Saved the tree image as images/tree_bank_marketing.png.

Interpreting Decision Rules

Read top splits from the tree and converted them into human-readable rules, for example:

Previous successful contacts and longer call duration → higher chance of subscription.

Very short calls with no previous contact → low chance of subscription.

Cellular contact in certain months with fewer campaign contacts → better subscription probability.

Results
Train accuracy: ~0.90

Test accuracy: ~0.90

The model does not show strong overfitting because train and test accuracies are very close.

Due to class imbalance, the model detects “no” better than “yes”; recall for term deposit subscribers is lower, which is important for business interpretation.

Key Learnings
How to build an interpretable Decision Tree model with scikit-learn.
​

How to handle multiple categorical variables using OneHotEncoder and ColumnTransformer.

Understanding:

Overfitting in trees and the role of max_depth.

Gini impurity as a node purity measure.

Basic ideas of pruning and decision boundaries for decision trees.
​

How to Run
Clone the repository:

bash
git clone <your_repo_linhttps://github.com/PranithaBokketi/task8-bank-marketing-subscription-prediction>.git

Install dependencies (example):


pip install -r requirements.txt
# or manually:
pip install pandas numpy scikit-learn matplotlib
Open the notebook:


marketing.ipynb
Run all cells to reproduce the analysis, model, and tree visualization.

