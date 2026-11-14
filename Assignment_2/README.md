# CS 4372: Assignment #2
## Assignment #2 - Using Trees
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

[ASSIGNMENT INSTRUCTIONS](Assign2_Instructions.pdf) <br>
[ASSIGNMENT REPORT](REPORT2.pdf)

Dataset: [UCI ML Repo's Wine Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality)

| Notebooks | Tasks |
|---|---|
| `Plain_Decision_Tree_Classifier.ipynb` | _Plain Decision Tree Classifier Regressor_ |
| `Random_Forest_Classifier.ipynb` | _Random Forest Classifier Regressor_ |
| `ada.ipynb` | _Adaboot Classifier Regressor_ |
| `xgb.ipynb` | _XGBoost Classifier Regressor_ |


### Summary 
In this assignment, we are comparing Plain Decision Tree Classifier, Random Forest Classifier, AdaBoost Classifier, and XGBoost Classifier. A Decision Tree uses a series of decision rules to classify data, while Random Forest combines multiple decision trees to improve accuracy and reduce overfitting. AdaBoost builds multiple weak learners sequentially, focusing more on incorrectly classified data, while XGBoost uses an optimized boosting approach to improve prediction performance.


### How To Run The Code
Each notebook runs on its own, on a local computer.
1. Open the notebook in Jupyter or VS Code.
2. Run the first code cell to install the packages, then restart the kernel if anything was installed.
3. Run all remaining cells in order.

#### Requirements
- Python 3.10 or newer, run through [Anaconda](https://www.anaconda.com/download) (the Decision Tree and Random Forest notebooks install graphviz with `%conda`)
- Packages (installed by the first code cell of each notebook):
```
pip install ucimlrepo pandas numpy seaborn matplotlib 
scikit-learn scikit-plot xgboost graphviz
conda install -c conda-forge python-graphviz
```

#### Origin of Data:
The dataset is loaded directly from the UCI ML Repository with `fetch_ucirepo(id=186)`, so no local paths are used:
https://archive.ics.uci.edu/dataset/186/wine+quality


## Assumptions
- Red and white wines are combined into one dataset of *6,497* samples.
- The quality score is converted into a binary target: quality of 7 or higher = good (1), otherwise not good (0). About *20%* of the wines are good, so the classes are imbalanced.

- **Decision Tree and Random Forest:**
  - Missing values are filled with the column mean (the dataset has none, so nothing changes).
  - Five attributes are kept based on their correlation with the target: alcohol, volatile acidity, density, chlorides, and citric acid. They are standardized before training.
  - The data is split *80/20* into training and testing sets (stratified, `random_state=5`), and results are reported on the test set.
  - GridSearchCV tunes the hyperparameters by accuracy, with *5*-fold (Decision Tree) and *10*-fold (Random Forest) cross-validation.

- **AdaBoost and XGBoost:**
  - All 11 attributes are used without scaling.
  - GridSearchCV tunes the hyperparameters with *5*-fold cross-validation on the full dataset, and results are reported on that same data.