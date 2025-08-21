# ⚡ Zelestra 2025 Hackathon – Solar Panel Efficiency Prediction  

## 📌 Overview  
This project was developed for the **Zelestra 2025 Hackathon**, where the challenge was to **predict the efficiency of solar panels** using environmental, operational, and installation-related data.  

We built a **hybrid ensemble machine learning pipeline** that combines **LightGBM**, **Histogram Gradient Boosting**, and **Ridge Regression** inside a **stacking framework**, with advanced feature transformations for robust and accurate efficiency predictions.  

---

## 🗂️ Dataset  

The dataset contained two files:  

- **train.csv** – Training data with features and target `efficiency`.  
- **test.csv** – Test data with the same features (without efficiency).  

### Key Features:  
- Environmental: `temperature`, `irradiance`, `humidity`, `wind_speed`, `pressure`, `cloud_coverage`  
- Operational: `voltage`, `current`, `module_temperature`, `soiling_ratio`, `maintenance_count`  
- Installation: `panel_age`, `string_id`, `error_code`, `installation_type`  
- **Target**: `efficiency`  

---

## ⚙️ Approach  

### 🔹 1. Data Preprocessing  
- Converted `wind_speed`, `pressure`, and `humidity` to numeric.  
- Label-encoded categorical variables: `string_id`, `error_code`, `installation_type`.  
- Handled missing values via **KNN imputation**.  

### 🔹 2. Feature Engineering  
- Generated **correlation heatmaps** to identify the most important features.  
- Selected features strongly correlated with `efficiency`.  
- Designed a **FeatureBlender transformer**:  
  - StandardScaler  
  - QuantileTransformer (normal distribution)  
  - Original + transformed features concatenated  

### 🔹 3. Model Building  
- **Hybrid Stacking Regressor**:  
  - Base learners:  
    - `LightGBM Regressor`  
    - `Histogram Gradient Boosting Regressor`  
  - Final learner: `RidgeCV`  
- Implemented using **Scikit-learn Pipelines** for clean workflow.  

### 🔹 4. Evaluation  
- Metrics:  
  - **Mean Squared Error (MSE)**  
  - **R² Score**  
  - **Mean Absolute Percentage Error (MAPE)**  
- Custom hackathon score function was also computed.  

---

## 🚀 Results  
- The hybrid stacking model achieved **robust accuracy in efficiency prediction**.  
- Strong generalization on test data.  
- Final predictions.
---

## 📂 Files in Repository  
- `train.csv` – Training dataset  
- `test.csv` – Test dataset  
- `zelestra.ipynb` – Main notebook with preprocessing, modeling, and prediction code  
---

## ▶️ How to Run  

1. Clone the repository:  
   ```bash
   git clone https://github.com/mondal-paushali03/zelestra-2025-hackathon.git
   cd zelestra-2025-hackathon ```
2. Upload datasets (train.csv, test.csv) in Colab or local environment.
3. Run the notebook:
   ```bash
   jupyter notebook hackathon_solution.ipynb```

---
## 📊 Tech Stack  

- **Python**  
- **Pandas, NumPy, Matplotlib, Seaborn** – EDA & Visualization  
- **Scikit-learn** – Preprocessing, Pipelines, Stacking  
- **LightGBM** – Boosting Model  
- **Google Colab** – Execution Environment
---

## Contact
For questions or suggestions, feel free to reach out at mondal.paushali384@gmail.com.

## License
This project is licensed under the MIT License.


