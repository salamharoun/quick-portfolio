# Data Analysis Report

## Pre-processing
Pre-processing (dimensionality reduction, transformations, and data cleaning) was handled appropriately. Missing data or "NaNs" were addressed by deleting 22 rows (7% of the data). This approach was chosen because removing NaNs directly or replacing them with other values could negatively impact clustering. 

For dimensionality reduction, no reduction was applied initially, as the observations were columns in the main dataset. Transformation was performed using z-scores before reducing dimensions for other analyses.

---

## Question 1: Preference Between Classical and Modern Art
- **Approach:** A Mann-Whitney U test was used since the data was ordinal and not normally distributed.
- **Method:** 
  - Ratings for classical and modern art were extracted into separate arrays.
  - Mann-Whitney U test results:
    - U = 38814531.5
    - p-value = 1.39e-87 (significant at α = 0.05)
  - Median scores: Classical = 5, Modern = 4.
- **Conclusion:** Classical art was preferred over modern art.

---

## Question 2: Preference Between Modern and Non-Human Art
- **Approach:** Mann-Whitney U test.
- **Results:** 
  - U = 19013098.0
  - p-value = 1.30e-243 (significant at α = 0.05).
- **Conclusion:** A significant difference exists in preferences between modern and non-human art.

---

## Question 3: Gender Differences in Art Preferences
- **Approach:** Mann-Whitney U test.
- **Results:** 
  - U = 68961959.5
  - p-value = 0.10113 (not significant).
- **Conclusion:** No significant preference difference between men and women.

---

## Question 4: Art Background and Preferences
- **Approach:** Mann-Whitney U test.
- **Results:** 
  - U = 65646419.5
  - p-value = 3.77e-08 (significant at α = 0.05).
  - Sample sizes: Art background = 16926, No art background = 8099.
- **Conclusion:** Users with an art background show significantly different preferences than those without.

---

## Question 5: Predicting Preferences from Energy Ratings
- **Approach:** Linear regression.
- **Results:** 
  - Mean cross-validation scores: [0.0504, 0.1467, -0.0259], mean = 0.057.
  - Mean squared error = 0.96 ± 0.15.
- **Conclusion:** Linear regression was not effective due to the ordinal nature of the data.

<img src="images/faultyRegression0.png?raw=true"/>

---

## Question 6: Predicting Preferences from Energy and Demographic Ratings
- **Approach:** Linear regression with cross-validation.
- **Results:** 
  - Mean cross-validation score = 0.05.
  - Mean squared error = 0.92 ± 0.12.
- **Conclusion:** Model accuracy was low due to ordinal and categorical predictors.

<img src="images/faultyRegression.png?raw=true"/>

---

## Question 7: Clustering Art Preferences and Energy Ratings
- **Approach:** K-means clustering with silhouette and elbow methods to determine optimal clusters.
- **Results:** 4 clusters identified.
- **Interpretation:** 
  - Red: Non-human art.
  - Green: Low-energy, high-preference classical art.
  - Orange: Modern art.
  - Blue: Intense classical art.

<img src="images/sScore.png?raw=true"/>
<img src="images/elbowMethod.png?raw=true"/>
<img src="images/clusters.png?raw=true"/>

---

## Question 8: Self-Worth and Art Preferences
- **Approach:** PCA on self-image ratings and linear regression.
- **Results:** 
  - Coefficient = -0.0032
  - Mean cross-validation score = -0.0512.
- **Conclusion:** No relationship between self-worth and art preference.

<img src="images/PCA_0.png?raw=true"/>
<img src="images/linearRegression.png?raw=true"/>

---

## Question 9: Dark Personality Traits and Preferences
- **Approach:** PCA on dark personality traits with linear regression.
- **Results:** 
  - Testing score = 0.086.
  - Callousness (3rd component) had the highest explanatory power (R² = 0.036).
- **Conclusion:** Callousness slightly predicts preferences, but overall model performance was poor.

<img src="images/PCA_1.png?raw=true"/>

---

## Question 10: Predicting Political Orientation
- **Approach:** Logistic regression with PCA-derived components as predictors.
- **Results:** 
  - AUC score = 0.68.
- **Conclusion:** The model reasonably predicts political orientation.

<img src="images/PCA.png?raw=true"/>
<img src="images/ROC_curve.png?raw=true"/>

---

