# NBA Fantasy Modelling & Optimisation Notebook

Author: **Ashkaan Gaurav Singh**

Entire Python notebook with the full analysis can be found in this repository in the file: **analysis.ipynb**.

---

## Tools

- Python  
- Pandas, NumPy  
- Scikit-learn  
- LightGBM  
- XGBoost  
- Matplotlib  
- Seaborn  
- PuLP  

---

## Overview

This notebook combines machine learning and optimisation techniques to simulate realistic NBA fantasy team construction across multiple seasons.

Historical NBA player statistics are used to predict next-season fantasy production, and these predictions are then fed into a constrained optimisation framework to construct optimal fantasy rosters under salary cap and positional constraints.

Multiple machine learning models are evaluated and combined using ensembling techniques to improve predictive performance and downstream roster construction quality.

---

## Deeper Dive

### Data Preparation & Feature Engineering

The dataset contains historical NBA player statistics, fantasy scoring metrics and salary information across multiple seasons.

Key preprocessing and feature engineering steps include:
- Cleaning and standardising player data  
- Handling positional information  
- Creating lag-based features using previous-season performance  
- Constructing next-season prediction targets  
- Engineering predictors such as:
  - Previous season FPPG  
  - Games played  
  - Shooting efficiency metrics  
  - Per-minute fantasy production  
  - Usage-related statistics  

The notebook uses a rolling forecasting setup where:
- Current season statistics are used to predict next-season fantasy production  
- Historical seasons are used as training data for future-season forecasting  

---

### Fantasy Scoring System

The ESPN fantasy scoring system is applied to convert raw NBA player statistics into:

- **Total Fantasy Points (TFP)**  
- **Fantasy Points Per Game (FPPG)**  

These values form the primary target variables for predictive modelling and optimisation.

---

### Predictive Modelling

Several machine learning models are implemented to predict future player fantasy production:

- Linear Regression  
- Elastic Net Regression  
- Random Forest  
- LightGBM (LGBM)  
- XGBoost  

Each modelling approach captures different characteristics of player performance:

- Linear/Elastic Net → interpretable baseline models with regularisation  
- Tree-based models → non-linear relationships and feature interactions  
- Boosting models → strong predictive performance on structured tabular data  

---

### Ensemble Model

An ensemble model is constructed by combining predictions from all individual models.

**Purpose:**
- Reduce model-specific bias  
- Improve robustness across seasons  
- Increase overall predictive reliability  

The ensemble model consistently produced the strongest overall predictive performance across multiple evaluation periods.

---

### Salary Cap Constrained Optimisation

A major component of the notebook is constructing optimal fantasy teams under realistic constraints using binary integer programming with PuLP.

The optimisation process:
- Uses predicted player fantasy production as the objective function  
- Applies salary cap constraints  
- Enforces fixed team sizes  
- Optionally incorporates positional roster requirements  

This transforms the project from a pure prediction problem into a realistic sports analytics optimisation task.

The optimisation problem is formulated similarly to:
- Knapsack optimisation  
- Binary integer programming  

---

### Team Construction & Backtesting

The notebook performs realistic season-by-season fantasy roster simulations by:

1. Using end-of-season player statistics  
2. Predicting next-season fantasy production  
3. Constructing an optimal fantasy roster using only pre-season information  
4. Comparing the generated roster against the true optimal roster once the season concludes  

This creates a realistic backtesting framework for evaluating:
- Predictive model quality  
- Roster construction quality  
- Downstream decision-making performance  

---

### Constraint Analysis

Fantasy teams are constructed under two different optimisation scenarios:

- No positional requirements  
- Position-constrained rosters  

This allows analysis of:
- How roster composition changes under additional constraints  
- The trade-offs introduced by positional requirements  
- Differences in achievable fantasy output  

---

### Model & Optimisation Evaluation

Models are evaluated using standard regression metrics including:
- Mean Absolute Error (MAE)  
- Root Mean Squared Error (RMSE)  
- R² Score  

However, the notebook also evaluates downstream optimisation quality using metrics such as:
- Percentage of optimal fantasy points achieved  
- Player overlap with the true optimal roster  
- Salary cap utilisation  
- Seasonal robustness across NBA eras  

This moves evaluation beyond traditional prediction metrics into practical decision-making performance.

---

### Key Findings

Some notable findings from the analysis include:

- Ensemble models consistently produced the strongest predictive performance  
- Optimised model-generated teams frequently achieved approximately 90–95% of the fantasy production of the theoretical optimal roster  
- Predicted rosters often shared significant overlap with the true optimal teams despite only using information available before the season began  
- Even when individual player predictions were imperfect, the optimisation framework was still able to identify many high-value players under salary constraints  

One particularly interesting observation was that relatively small player-level prediction errors did not necessarily translate into large roster-level performance losses once optimisation constraints were applied.

---

### Visualisation & Insights

Visualisations are used extensively throughout the notebook to:
- Compare predicted vs actual fantasy production  
- Analyse model performance across seasons  
- Explore feature importance for tree-based models  
- Compare constrained vs unconstrained roster construction  
- Evaluate optimisation quality over time  
- Analyse player overlap between predicted and true optimal rosters  

These visualisations help interpret both:
- Model behaviour  
- Practical fantasy roster construction outcomes  

---

## Key Takeaways

- Ensemble models improve predictive robustness over individual models  
- Tree-based and boosting approaches capture complex player performance patterns effectively  
- Incorporating salary and roster constraints transforms the problem from prediction into realistic optimisation  
- Downstream optimisation quality can remain strong even when player-level forecasts are imperfect  
- Data-driven fantasy roster construction can achieve performance close to the theoretical optimum using only historical information  

---
