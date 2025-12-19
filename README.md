# **Concrete Compressive Strength Prediction**

Random Forest Regression with OOB Validation

---

## **Project Overview**

- This project predicts **concrete compressive strength (MPa)** using mix composition and curing age.
- The goal is to demonstrate **data-driven model selection**, **careful validation**, and **interpretable machine learning** on a small, real-world engineering dataset.
- Rather than aggressive hyperparameter tuning, the project emphasizes **exploratory analysis**, **bias–variance awareness**, and **generalization stability**.

---

## **Dataset**

- **Source:** Yeh Concrete Compressive Strength Dataset
- **Sample:** 1,030
- **Features:** 8 numerical input variables
- **Target:** `csMPa` (Concrete Compressive Strength in MPa)
- **Missing Values:** None
- **Categorical Variables:** None
- **Input Features**
  - Cement
  - Blast Furnace Slag
  -Fly Ash
  - Water
  - Superplasticizer
  - Coarse Aggregate
  - Fine Aggregate
  - Age (days)

---

## **Exploratory Data Analysis (EDA)**

Key findings from EDA:

- Strong **non-linear relationships** and **interaction effects**
- Right-skewed target distribution with **physically meaningful high-strength values**
- Zero-inflated features (slag, fly ash, superplasticizer)
- Linear correlations underestimate true feature influence

These insights motivated the use of **tree-based regression models** instead of purely linear approaches.

---

## **Modeling Approach**

### **Baseline Model**

**Linear Regression**

- Test R²: 0.63
- RMSE: ~9.8 MPa
- MAE: ~7.7 MPa

Used to establish a simple, interpretable benchmark.

### **Final Model**

**Random Forest Regressor**

- n_estimators = 500
- min_samples_leaf = 3
- oob_score = True
- No aggressive hyperparameter tuning

This configuration balances model capacity and generalization stability, guided by empirical diagnostics rather than grid search.

---

## **Model Performance**

| Metric     | Linear Regression | Random Forest |
| ---------- | ----------------- | ------------- |
| Test R²    | 0.63              | **0.87**      |
| RMSE (MPa) | 9.80              | **5.83**      |
| MAE (MPa)  | 7.75              | **4.25**      |
| OOB R²     | —                 | **0.90**      |

**Key takeaway:**

Random Forest captures non-linear and interaction effects, reducing prediction error by ~40% compared to the linear baseline.

---

## **Feature Importance Insights**

Feature importance analysis shows:
- **Age** and **cement** are the dominant predictors
- **Water** plays a strong negative, interaction-driven role
- **Slag** and **superplasticizer** have moderate, conditional importance
- Aggregates and fly ash contribute less marginally

These results align with both **EDA findings** and **domain knowledge**.

---

## **Limitations**

- Small dataset (~1k samples)
- No external validation dataset
- Limited extrapolation beyond observed ranges
- Feature importance reflects model reliance, not causality

---

## **Conclusion**

This project demonstrates how **EDA-driven modeling decisions** lead to robust and interpretable results.
By prioritizing generalization over over-tuning and validating performance carefully, the final Random Forest model provides reliable predictions for concrete compressive strength while remaining transparent and defensible.

---

## **Libraries used**

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

---

## **How to Run**

1. Clone the repository:
```bash
git clone https://github.com/PranayDomal/Random_Forest_Regression.git
```
2. Navigate to the folder:
```bash
cd Random_Forest_Regression
```
3. Run the notebook:
```bash
jupyter notebook Concrete_Strength_regression.ipynb
```

---

## **Project Structure**

├── Concrete_Data_Yeh.csv
├── Concrete_Strength_regression.ipynb
├── README.md

---

## **Author**

https://www.linkedin.com/in/pranay-domal-a641bb368/
