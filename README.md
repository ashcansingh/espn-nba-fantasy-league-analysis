# NBA Fantasy Modelling & Optimisation Notebook

## Overview

This notebook builds predictive models to estimate NBA player fantasy performance and uses these predictions to construct optimal fantasy teams under salary cap constraints. Multiple machine learning models are compared and combined via ensembling to improve prediction accuracy.

---

## Deeper Dive

### Data Preparation & Feature Engineering  
The dataset contains historical NBA player statistics and salary information across multiple seasons.

Key preprocessing steps include:
- Cleaning and standardising player data  
- Handling positional information  
- Creating lag-based features (e.g. previous season performance)  
- Engineering relevant predictors such as:
  - Previous FPPG  
  - Games played  
  - Efficiency metrics  

These steps ensure the data is suitable for both predictive modelling and optimisation.

---

### Fantasy Scoring System  
The notebook applies the ESPN fantasy scoring system to convert raw player statistics into:

- **Total Fantasy Points (TFP)**  
- **Fantasy Points Per Game (FPPG)**  

This creates a consistent target variable for modelling player performance.

---

### Predictive Modelling  

A range of models are implemented to predict future player performance (e.g. next-season FPPG or total fantasy output):

- Linear Regression  
- Elastic Net Regression  
- Random Forest  
- LightGBM (LGBM)  
- XGBoost  

Each model captures different aspects:
- Linear/Elastic Net → interpretable baseline + regularisation  
- Tree-based models → non-linear relationships and interactions  
- Boosting models → strong predictive performance on structured data  

---

### Ensemble Model  

An ensemble model is constructed by combining predictions from all individual models.

**Purpose:**
- Reduce model-specific bias  
- Improve robustness  
- Achieve better overall predictive accuracy  

This reflects a practical approach used in real-world predictive systems.

---

### Model Evaluation  

Models are evaluated using standard regression metrics such as:
- Mean Absolute Error (MAE)  
- Root Mean Squared Error (RMSE)  
- R² Score  

Comparisons across models allow identification of:
- Best-performing individual model  
- Gains from ensembling  

---

### Salary Cap Constrained Optimisation  

A key component of the notebook is constructing **optimal fantasy teams under a salary cap constraint**.

This involves:
- Using predicted player performance as the objective  
- Incorporating salary as a constraint  
- Selecting a fixed number of players  

The problem is formulated as an optimisation task similar to:
- Knapsack / integer programming  

**Outcome:**
- Selection of the highest-value team given budget limitations  
- More realistic team construction compared to unconstrained selection  

---

### Team Selection Strategy  

The notebook:
- Ranks players based on predicted performance  
- Applies constraints (salary cap, team size, positions if applicable)  
- Constructs optimal lineups using model outputs  

This bridges the gap between **prediction → decision-making**, which is a key strength of the project.

---

### Visualisation & Insights  

Visualisations are used to:
- Compare model predictions vs actual values  
- Analyse feature importance (for tree-based models)  
- Explore relationships between salary and performance  

These help interpret both:
- Model behaviour  
- Practical implications for team building  

---

## Key Takeaways  

- Ensemble models improve predictive reliability over individual models  
- Tree-based and boosting models capture complex player performance patterns effectively  
- Incorporating salary constraints transforms the problem from prediction to optimisation  
- Data-driven team selection significantly improves decision quality under budget limits  

---

## Tools & Libraries  

- Python  
- Pandas, NumPy  
- Scikit-learn  
- LightGBM  
- XGBoost  
- Matplotlib  
- Seaborn  

---

## Future Improvements  

- Incorporate injury and availability features  
- Model games played separately for better total point prediction  
- Add positional constraints explicitly into optimisation  
- Explore advanced ensembling (stacking instead of averaging)  
