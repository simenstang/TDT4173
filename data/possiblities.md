Feature engineering is indeed a powerful method for improving model performance, especially when facing challenging datasets with issues such as gaps and repeated values.

Given the specifics of your dataset and the nature of PV predictions, I'd prioritize the following feature engineering techniques:

1. **Time Features**: Despite other issues, the temporal nature of the dataset can often play a big role in predictions.
    - Extract hour, day, month, and year.
    - Create binary features for weekends vs. weekdays, as solar irradiance and consumption patterns differ.
    - Seasons can influence solar irradiance significantly. Create a feature denoting which season the day belongs to.

2. **Sun-related Features**:
    - As PV generation heavily depends on the sun's position, create features using sun_azimuth and sun_elevation.
        - Binary feature for when sun is above a certain elevation threshold.
        - Cosine and sine transformations of sun_azimuth can provide more detailed info about the sun's position.

3. **Weather Interaction Features**:
    - Interaction between clear sky radiation and the sun's elevation can be crucial. For example, high clear sky radiation when the sun is at peak might lead to higher PV output.
    - Consider interactions with cloud cover, as it can affect how much radiation reaches the PV panels.

4. **Aggregation**:
    - Create rolling averages or sums, especially for radiation and temperature-related variables. Even if lag features don't work well, a smoothed rolling average might capture broader trends.

5. **Weather Patterns & Anomalies**:
    - If there's a sudden change in a particular weather variable, it might be an indicator of shifting weather patterns, which could influence PV output. Look for sudden drops or increases in parameters like air pressure or humidity.

6. **Handling Shadows**:
    - The 'is_in_shadow:idx' can be crucial. Consider using it as a multiplicative factor with radiation measurements.

Given the challenges:

- **Handling Gaps**: If imputation doesn't work well and the gaps are too large to fill, it might be beneficial to treat your dataset as multiple smaller time series. This way, each segment with continuous data is treated separately. While you lose the ability to capture long-term trends, you'll have more accurate short-term predictions.

- **Model Choice**: Consider models that can inherently handle missing values, like XGBoost. These models can utilize the information present in other features when some are missing.

- **Model Validation**: When you have gaps in your dataset, traditional time series cross-validation methods might not be the best choice. Consider using a walk-forward validation or time series split, which acknowledges these gaps.

Lastly, after every feature engineering step, monitor how each feature impacts model performance. This can be achieved by tracking feature importances (in tree-based models) or through methods like SHAP (SHapley Additive exPlanations) to understand the effect of each feature on the predictions.