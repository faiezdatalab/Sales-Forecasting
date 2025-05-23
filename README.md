# Sales-Forecasting

#### Sales Forecasting Project

#### Project Overview
This project focuses on improving **sales forecasting accuracy** by leveraging historical sales data. The core objective is to predict the **Close_Value** of sales opportunities using machine learning, with a specific focus on **Random Forest Regression**.

---

#### Dataset Overview
The dataset includes the following key columns:
- `Account`
- `Opportunity_ID`
- `Sales_Agent`
- `Deal_Stage`
- `Product`
- `Created_Date`
- `Close_Date`
- `Close_Value`

---

#### Data Preprocessing
To prepare the data for modeling, the following preprocessing steps were performed:

- **Target Encoding** of categorical variables based on average `Close_Value`:
  - `Account`
  - `Opportunity_ID`
  - `Sales_Agent`
  - `Deal_Stage`
  - `Product`
- Calculated `Time_to_Close` using the difference between `Close_Date` and `Created_Date`
- Analyzed temporal trends in sales closing time

---

#### Correlation Analysis
We evaluated the correlation between encoded features and the target (`Close_Value`):

| Feature                    | Correlation |
|---------------------------|-------------|
| Product_TargetEncoded     | 0.70        |
| Deal_Stage_TargetEncoded  | 0.50        |
| Account_TargetEncoded     | 0.30        |
| Sales_Agent_TargetEncoded| 0.20        |

**Top 2 features** were used for the baseline regression model.

---

#### Model Training – Random Forest Regressor
- Selected Model: **RandomForestRegressor**
- Feature set:  
  - `Product_TargetEncoded`  
  - `Deal_Stage_TargetEncoded`
- Train-Test Split: 80/20

#### Model Performance
| Metric        | Value         |
|---------------|---------------|
| MSE           | 64,498.78     |
| R² Score      | 0.98          |
| MAE           | 150.00        |

---

#### Hyperparameter Optimization
- **Method**: `GridSearchCV`
- **Best Parameters**:
  - `max_depth`: 10
  - `max_features`: 'auto'
  - `min_samples_leaf`: 1
  - `min_samples_split`: 5
  - `n_estimators`: 150

#### Cross-Validation Results
- **MSE across 5 folds**: 71,636.73 ± 9,377.15

---

#### Model Saving and Loading
The final optimized model was saved using `joblib`

### Conclusion

This project successfully demonstrates how machine learning, particularly Random Forest Regression, can be used to significantly enhance sales forecasting accuracy.

#### Key Outcomes:
   - Model Accuracy:

* R² Score: 0.98, indicating that 98% of the variance in Close_Value is explained by the model.

* Mean Absolute Error (MAE): 150.00, showing the average prediction error in currency units.

* Mean Squared Error (MSE): 64,498.78, which reflects strong performance given the scale of sales values.

* Cross-Validation MSE: 71,636.73 ± 9,377.15, proving the model is stable across unseen subsets of data.

  - Most Influential Features:

* Product_TargetEncoded: High correlation (0.7) and impact on deal value.
* Deal_Stage_TargetEncoded: Directly tied to sales pipeline progression, with a strong correlation (0.5).

  - Business Impact:

* Accurate Forecasting: Sales leaders can use the model to predict future revenue with high confidence.
* Informed Strategy: Helps identify which products and deal stages yield the highest returns.
* Faster Decisions: Reduces manual estimation and speeds up sales pipeline analysis.

  - Technical Impact:

* Efficient use of Target Encoding on high-cardinality categorical variables ensured better model generalization.
* Feature selection driven by correlation a-nalysis streamlined model complexity while maintaining accuracy.
* Hyperparameter tuning and cross-validation ensured robustness and minimized overfitting.

In summary, this project delivers a high-performing, interpretable, and reusable model that aligns with both business goals and data science best practices. It sets a strong foundation for integrating machine learning into sales operations and forecasting systems.



