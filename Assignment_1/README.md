# CS 4372: Assignment #1
## Assignment #1 - Linear Regression Analysis
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

[ASSIGNMENT INSTRUCTIONS](Assign1_Instructions.pdf) <br>
[ASSIGNMENT REPORT](REPORT1.pdf)

Dataset: [UCI ML Repo's Automobile Dataset](https://archive.ics.uci.edu/dataset/10/automobile)


| Notebooks | Tasks |
|---|---|
| `SGDRegressor.ipynb` | _SGDRegressor_ library using scikit-learn |
| `ols.ipynb` | _OLS_ library of Statsmodels |


### Summary
In this assignment, we are comparing OLS vs an SGD regressor. An OLS model is a linear regression model that performs Gaussian elimination on a matrix to find the line of best fit and performs this action in O(n^3). An SGD regressor traces curves using derivatives to find a local minima for a line of best fit. It can do this in O(n) time, it tends to perform slightly worse than OLS, but can achieve this in much faster time.



### How To Run The Code
Since we do all the pip installs at the beginning the code should just run as typed. We don't do any external imports outside of what has already been installed at the beginning.

Each notebook runs on its own, on a local computer.
1. Open the notebook in Jupyter or VS Code.
2. Run the first code cell to install the packages, then restart the kernel if anything was installed.
3. Run all remaining cells in order.

#### Requirements
- Python 3.10 or newer
- Packages (installed by the first code cell of each notebook):
```
pip install ucimlrepo pandas numpy seaborn matplotlib scikit-learn statsmodels
```

#### Origin of Data
The dataset is loaded directly from the UCI ML Repository with `fetch_ucirepo(id=10)`, so no local paths are used:
https://archive.ics.uci.edu/dataset/10/automobile




### Assumptions
- Missing numeric values are filled with the column mean. `num-of-doors` is filled with its most common value, because a door count can only be 2 or 4.
- Text (categorical) attributes are converted to numbers with one-hot encoding.
- The data is split *80/20* into training and testing sets, and results are reported on the test set.
- **SGDRegressor:**
  - Six attributes are kept based on their correlation with the target: engine size, curb weight, horsepower, width, highway mpg, and city mpg. They are standardized before training.
  - The split uses `random_state=5`.
  - Hyperparameters are tuned with a grid of *288* combinations of penalty, alpha, l1 ratio, learning rate, max iterations, and loss.
- **OLS:**
  - All attributes are used without scaling, plus an intercept term.
  - The split uses `random_state=42`.