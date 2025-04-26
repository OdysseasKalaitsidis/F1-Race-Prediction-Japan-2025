# Predicting 2025 Japanese GP Race Results with Machine Learning

## Overview
This project uses machine learning to predict the 2025 Japanese Grand Prix race results based on historical race data (2022-2024). It leverages data from the FastF1 API and a Random Forest model to make predictions about driver finishing positions.

## Project Structure

1. **Setup and Imports**
    - Libraries: `fastf1`, `pandas`, `numpy`, `sklearn`, `matplotlib`.
    - Enable caching for FastF1 data.

2. **Driver List**
    - Contains the abbreviations of drivers competing in 2025.

3. **Fetching Race Data**
    - The `race_results()` function retrieves race results for the Japanese GP from 2022 to 2024.
    - For each year, the following data is collected per driver:
        - Finishing position
        - Total race time
        - Average lap time

4. **Data Cleaning**
    - Missing values (e.g., drivers who did not finish) are filled with a default high value (e.g., 50).

5. **Model Training**
    - **Features:** Positions, total times, and average lap times from 2022 to 2024.
    - **Target:** 2024 race position is used as a proxy target to simulate predicting future performance.
    - **Model:**
        - A `Pipeline` is built with a `StandardScaler` for feature normalization and a `RandomForestRegressor`.
        - The model is trained to learn the relationship between past race metrics and the final position.

6. **Prediction**
    - After training, the model predicts scores for each driver for 2025.
    - Drivers are ranked based on these scores to generate the final predicted order.

7. **Visualization (Optional)**
    - A horizontal bar chart shows the predicted finishing positions for the 2025 Japanese GP.

## Model Details

- **Algorithm:** Random Forest Regressor
- **Reason for Choice:**
    - Handles small datasets well.
    - Captures nonlinear relationships.
    - Robust to overfitting compared to simpler models.
- **Preprocessing:**
    - Scaling features to standardize inputs.
    - Filling missing data with default values to avoid training errors.

## Limitations
- Only the Japanese GP from the past three seasons is used.
- No qualifying, practice, or weather data are included.
- Assumes driver/team performance is relatively stable year-to-year.
- Does not account for mechanical failures, crashes, or major driver/team changes.

## Possible Improvements
- Incorporate qualifying and free practice session data.
- Add pit stop strategies and weather conditions.
- Use additional seasons (e.g., 2021, 2020) if relevant.
- Try advanced models (e.g., Gradient Boosting, XGBoost).
- Fine-tune hyperparameters for better performance.

## Conclusion
This project provides a basic yet functional machine learning pipeline to predict F1 race outcomes. It serves as a foundation for more advanced motorsport analytics projects, using accessible historical data and beginner-friendly machine learning tools.

