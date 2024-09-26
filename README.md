# EV Analysis: Exploratory Data Analysis with 'Price' as the Target Variable

## **1.Categorical Variable Analysis**

![Screenshot 2024-09-25 220441](https://github.com/user-attachments/assets/48a704ed-fa07-4c93-afda-17442b02dcc0)

### General Observations - Brand:
- **Porsche** has the highest mean and median prices, suggesting it's a more premium brand with a wide range of prices. The high standard deviation indicates significant price variation across different models.
- **Mercedes** also has a wide range of prices, but with a lower median than Porsche, suggesting it offers more mid-range options alongside its luxury models.
- **Opel** and **Peugeot** are more affordable brands, with lower means and standard deviations, indicating more consistent, tightly clustered prices.
- **Audi** sits somewhere in the middle, with moderate variation in prices but with some high-end vehicles.

### General Observations - Drive:
- **All Wheel Drive** vehicles have the highest mean price (€109,591) and the widest price range, with a maximum of €191,096. The high standard deviation indicates substantial variation in prices across models with this drive type. The median (€111,679) is close to the mean, indicating a relatively symmetric distribution.
- **Rear Wheel Drive** vehicles have a mean price of €83,610, with a median higher than the mean (€89,351), suggesting a slight left skew, meaning that the more expensive models may be pulling the median higher. The standard deviation (€20,285) shows moderate price variation.
- **Front Wheel Drive** vehicles are the most affordable, with the lowest mean (€54,008) and median (€53,640). They also have the smallest standard deviation (€10,480), indicating that prices are tightly clustered and consistent across models.
- In general, **All Wheel Drive** vehicles tend to be the most expensive and varied in price, while **Front Wheel Drive** vehicles are more affordable with less price variation.

### ANOVA Results

#### 1. ANOVA Result for Brands:
- **F-statistic:** 23.84
- **p-value:** 1.38e-13 (or 0.0000000000001376)

#### 2. ANOVA Result for Drive Types:
- **F-statistic:** 43.77
- **p-value:** 3.36e-14 (or 0.0000000000000336)

### Interpretation:

#### 1. Brands:
- The **F-statistic** of 23.84 indicates a significant difference between the means of prices across different brands.
- The **p-value** of 1.38e-13 is **extremely low**, much lower than the common significance level of 0.05. This suggests that there is **strong evidence** to reject the null hypothesis (which states that all brands have the same average price).
- **Conclusion:** The price of electric vehicles **varies significantly** between different brands.

#### 2. Drive Types:
- The **F-statistic** of 43.77 suggests that the difference in the means of prices between different drive types is even more pronounced.
- The **p-value** of 3.36e-14 is also much lower than 0.05, indicating that the null hypothesis (that prices are the same for all drive types) can be rejected.
- **Conclusion:** There is a **significant difference** in prices between different drive types (e.g., All Wheel Drive vs. Front Wheel Drive).

## **2. Numerical Variable Analysis**
![Screenshot 2024-09-25 221108](https://github.com/user-attachments/assets/caeb4bf8-4b63-4db4-976d-a45660c387d0)

![show relationship](https://github.com/user-attachments/assets/1bb3ac38-08b7-4b52-8925-4fb25f984ad6)

![show concentration](https://github.com/user-attachments/assets/119a8841-4a11-4a8d-9c02-62c1b1076477)

## 3. Preliminary Multiple Linear regression Predict Price
- **Question:** How sensitive is the price to all variables?
- **Objective:** Determine the factors influence price.
  
![preliminary regression](https://github.com/user-attachments/assets/c0a2e40a-1724-454f-8fcf-0d378493f37e)

## Key Takeaways from the OLS Regression Results

1. **R-squared = 0.821**:
   - The model explains about **82.1%** of the variance in the dependent variable (`PriceinGermany`).
   - This indicates a strong model fit, though not perfect.

2. **Adjusted R-squared = 0.815**:
   - The adjusted R-squared accounts for the number of predictors in the model.
   - It's still a good value, indicating the model generalizes well beyond the training data.

3. **F-statistic and p-value (Prob > F)**:
   - **F-statistic = 137.1**: The independent variables collectively have a significant relationship with the dependent variable.
   - **p-value (4.05e-95)**: The very small p-value indicates the overall model is highly significant.

4. **Significant Coefficients (p < 0.05)**:
   - **x1 (`Usable Battery (kWh)`):** Positive coefficient (**964.67**), suggesting that an increase in battery capacity is associated with an increase in price.
   - **x2 (`Acceleration (sec)`):** Positive coefficient (**2020.36**), meaning faster acceleration (lower time in seconds) leads to higher prices.
   - **x3 (`TopSpeed (km/h)`):** Positive coefficient (**351.16**), meaning higher top speeds lead to higher prices.
   - **x8 (`Drive_encoded`):** Positive coefficient (**5904.15**), showing that a higher encoding (likely all-wheel drive) increases price significantly.
   - **x9 (`Brand_encoded`):** Positive coefficient (**0.6994**), meaning that brands with a higher average price (target encoded) are associated with higher vehicle prices.

5. **Non-Significant Variables (p > 0.05)**:
   - **x4 (`Range (km)`), x5 (`Efficiency (Wh/km)`), x6 (`FastChargeSpeed (km/h)`), x7 (`NumberofSeats`)**:
     - These variables do not have a statistically significant impact on price.

6. **Multicollinearity**:
   - **Condition Number = 1.84e+06**: This large condition number indicates potential multicollinearity. 
   - Multicollinearity can cause unreliable coefficient estimates and inflate standard errors.

7. **Durbin-Watson = 1.300**:
   - This value tests for autocorrelation in the residuals. Since 1.300 is below 2, there may be some positive autocorrelation in the residuals, though it is not severe.

8. **Skew and Kurtosis**:
   - **Skew = 0.593**: Indicates some asymmetry in the distribution of residuals.
   - **Kurtosis = 4.823**: Indicates heavier tails in the residual distribution (more outliers).

---

## Next Steps:

1. **Address Multicollinearity**:
   - Compute the **Variance Inflation Factor (VIF)** and remove or combine variables with high multicollinearity (VIF > 10).

2. **Recheck Model Fit**:
   - After addressing multicollinearity, refit the model to see if the coefficients and their significance improve.

3. **Consider Transformations**:
   - Consider **log transformations** to handle skewness and make the residuals more normally distributed.

4. **Residual Analysis**:
   - Perform **residual diagnostics** to check if the residuals are normally distributed and if there are any patterns in the residuals.






