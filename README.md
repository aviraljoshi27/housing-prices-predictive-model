# housing-prices-predictive-model
📈 Housing Price Prediction with Linear Regression This project demonstrates a complete end-to-end pipeline to predict housing prices using linear regression. It includes data preprocessing, feature engineering, model building with statistical techniques, multicollinearity checks using VIF, and evaluation on unseen data.

🏡 Housing Price Prediction - Linear Regression
This project performs a linear regression analysis on housing data to predict property prices using various numerical and categorical features.

📂 Dataset

Source: Housing.csv
Columns include features such as:
Area, Bedrooms, Bathrooms, Stories, Parking, Main road access, Guest room availability, Basement, Hot water heating, Air conditioning, Furnishing status

Target variable: price

📊 Libraries Used:
-pandas, numpy for data manipulation
-matplotlib.pyplot, seaborn for visualization
-sklearn for preprocessing and evaluation
-statsmodels for statistical modeling

🔄 Workflow Summary:

1. Data Understanding:
-Load and inspect the dataset
-Visualize numerical features using pairplot
-Analyze categorical variables using boxplot

2. Data Preparation:
-Encode binary categorical variables (yes/no to 1/0)
-Create dummy variables for multi-class columns (e.g., furnishingstatus)
-Split the data into training (70%) and test (30%)
-Normalize features using Min-Max scaling

🔧 Data Preprocessing Methods:
fit()
-Computes the required statistics (e.g., mean and std for normalization)
-Use only on the training set
-Example: scaler.fit(X_train)

transform()
-Applies the transformation using parameters computed by fit()
-Use on both training and test sets (after fitting on training data)
-Example: scaler.transform(X)

fit_transform()
-Combines both fit() and transform() in one step
-Only use on training data
-Example: scaler.fit_transform(X_train)

3. Model Building:
-Start with one feature (area), then iteratively add more
-Use statsmodels.api.OLS to build linear regression models
-Assess model performance with:
-p-values for feature significance
-VIF (Variance Inflation Factor) for multicollinearity

📐 Feature Selection Strategy:
❌ Remove if P-Value is High and VIF is High
⚠ Remove and check again if P-Value is High and VIF is Low
⚠ Remove if VIF > threshold (e.g., 5 or 10) if P-Value is Low and VIF is High
✅ Keep if P-Value is Low and VIF is Low

4. Final Model Equation
price = 0.0357 
      + 0.2347 * area 
      + 0.1965 * bathrooms 
      + 0.1178 * stories 
      + 0.0488 * mainroad 
      + 0.0301 * guestroom 
      + 0.0239 * basement 
      + 0.0864 * hotwaterheating 
      + 0.0665 * airconditioning 
      + 0.0629 * parking 
      + 0.0596 * prefarea 
      - 0.0323 * unfurnished

5. Model Evaluation:
-Residual analysis to confirm assumptions
-Evaluate R-squared on both train and test sets
-Confirm no data leakage and good generalization

✅ Results:
-Final model has statistically significant features
-No multicollinearity (VIF < 5 for all features)
-Residuals are normally distributed
-Test set performance confirms good generalization

📌 Notes:
-Always fit scalers and encoders on train data only
-Use transform on test data to prevent data leakage

📎 To Run:
Ensure Housing.csv is in your working directory.
Run the notebook cells in sequence.

Made with ❤️ using Python, Statsmodels, and Scikit-learn

