# Geometric Median Optimization (Weiszfeld's Algorithm)
**Author:** Arman Azadi
**Institution:** Iran University of Science and Technology (IUST)

## 📌 Project Overview
This project solves the **Geometric Median** problem (also known as the Fermat Point problem) for a set of 2D data points. Unlike the Arithmetic Mean which minimizes the sum of squared Euclidean distances (L2 norm), the Geometric Median minimizes the sum of distances (L1 norm):

$$\min_{\mu} \sum_{i=1}^{N} || x_i - \mu ||_2$$

This property makes the Geometric Median significantly more **robust to outliers** than the standard mean. The solution is approximated using **Weiszfeld's Algorithm**, an iterative optimization method.

## 🔬 Methodology
The project implements the optimization pipeline from scratch in Python:

### 1. Algorithm: Weiszfeld's Iterative Method
The algorithm updates the estimate $\mu$ at each step $k$ using a weighted average of the data points, where weights are inversely proportional to the distance from the current estimate:

$$\mu_{k+1} = \frac{\sum_{i=1}^{N} \frac{x_i}{||x_i - \mu_k||}}{\sum_{i=1}^{N} \frac{1}{||x_i - \mu_k||}}$$

* **Initialization:** The Arithmetic Mean is used as the starting point ($\mu_0$).
* **Stopping Condition:** The loop terminates when the change in position $||\mu_{k+1} - \mu_k||$ falls below a threshold ($\epsilon = 1e-5$).

### 2. Dataset
* **Source:** `spatial_data.mat`
* **Structure:** 200 data points in a 2D Euclidean space.

## 📊 Results & Analysis
The implementation was evaluated based on convergence speed and solution accuracy.
*(See `Optimization_Report.docx` for full details)*

* **Robustness:** The results demonstrate that the Geometric Median (Red point in plots) is located centrally within the dense data cluster, whereas the Arithmetic Mean (Green point) is pulled away by outliers.
* **Convergence:** The objective function $D(\mu)$ decreases monotonically, confirming the convex nature of the problem and the stability of Weiszfeld's method.

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Scientific Computing:** `NumPy` (Vectorized operations), `SciPy` (Loading .mat files)
* **Visualization:** `Matplotlib` (Scatter plots and convergence curves)

## 🚀 Usage
1.  Clone the repository:
    ```bash
    git clone [https://github.com/armanazadi/geometric-median-optimization.git](https://github.com/armanazadi/geometric-median-optimization.git)
    ```
2.  Run the notebook:
    ```bash
    jupyter notebook geometric_median_solver.ipynb
    ```
