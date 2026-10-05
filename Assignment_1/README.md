# CS 4372: Assignment #1
## Assignment #1 - Linear Regression Analysis
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

Dataset: [UCI ML Repo's Automobile Dataset](https://archive.ics.uci.edu/dataset/10/automobile)

### Summary
In this assignment, we are comparing OLS vs an SGD regressor. An OLS model is a linear regression model that performs Gaussian elimination on a matrix to find the line of best fit and performs this action in O(n^3). An SGD regressor traces curves using derivatives to find a local minima for a line of best fit. It can do this in O(n) time, it tends to perform slightly worse than OLS, but can achieve this in much faster time.


### How To Run The Code
Since we do all the pip installs at the beginning the code should just run as typed. We don't do any external imports outside of what has already been installed at the beginning.
