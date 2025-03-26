# 🛒 Sales Forecasting using Machine Learning

## 📌 Project Overview
This project aims to develop a **sales forecasting model** that predicts future sales for thousands of product families across multiple stores. We analyze historical sales data along with external factors like **holidays, promotions, and oil prices** to build an accurate forecasting system.  

This project includes:
- ✅ **Data Cleaning & Feature Engineering**
- ✅ **Exploratory Data Analysis (EDA)**
- ✅ **Model Training & Evaluation (ARIMA, XGBoost, LightGBM, LSTM)**
- ✅ **Feature Importance Analysis (SHAP)**
- ✅ **Final Insights & Business Recommendations**

---

## 📂 Dataset Description
The dataset consists of multiple CSV files:

| File Name              | Description |
|------------------------|-------------|
| `train.csv`           | Historical sales data |
| `test.csv`            | Test set for future predictions |
| `stores.csv`          | Store metadata (location, cluster info) |
| `oil.csv`             | Daily oil prices (economic impact) |
| `holidays_events.csv` | Public holidays, promotions, & special events |

### **Target Variable:** `sales` (Daily sales of each product family in each store)

---

## ⚙️ Project Workflow
### **📌 1. Data Preprocessing & Feature Engineering**
- **Handled Missing Values:** Used interpolation for oil prices, filled missing `onpromotion` values as `0`.
- **Merged Data Sources:** Combined `stores.csv`, `oil.csv`, and `holidays_events.csv` into the main dataset.
- **Created New Features:**
  - **Time-based:** `month`, `day_of_week`, `is_weekend`
  - **Event-based:** `is_holiday`, `is_promotion`, `is_payday`
  - **Rolling statistics:** `sales_MA7`, `sales_MA30`, `sales_Lag7`, `sales_Lag30`

### **📌 2. Exploratory Data Analysis (EDA)**
- **Visualized sales trends** and identified seasonality.
- **Analyzed holiday impact** on sales.
- **Checked correlations** between oil prices and sales.
- **Identified anomalies** and demand fluctuations.

### **📌 3. Model Training & Evaluation**
We trained **five models** and compared their performance:

| Model      | RMSE  | MAE   | R² Score |
|------------|-------|-------|---------|
| **Naïve Forecasting** | 293.51 | 67.87 | 0.91 |
| **ARIMA** | 656.41 | 458.49 | -0.16 |
| **XGBoost** | 104.27 | 25.65 | 0.98 |
| **LightGBM** | **102.64** | **25.33** | **0.98** |
| **LSTM (Deep Learning)** | 142.57 | 50.19 | 0.96 |

### **🏆 Best Model: LightGBM**
✅ **Lowest RMSE (102.64) & MAE (25.33)**  
✅ **Highest R² Score (0.98)** → Explains 98% of variance in sales  

---



### **🔹 Top Features**
1. `onpromotion` → **Most influential** (Sales increase significantly during promotions)  
2. `sales_Lag7` & `sales_Lag30` → **Past sales are strong predictors**  
3. `is_holiday` → **Holidays lead to high sales spikes**  
4. `dcoilwtico` → **Oil prices have a weak indirect effect on sales**  

---

## 🔍 **Business Insights & Recommendations**
### **📈 Key Findings**
- 📅 **Holidays & promotions significantly boost sales.**
- 📉 **Past sales data (lag features) is the strongest predictor.**
- ⛽ **Oil prices impact overall sales patterns (economic influence).**
- 🏬 **Store clusters show different demand patterns (regional effects).**

### **💡 Business Strategies**
✔ **Optimize Inventory Management** → Stock up before holidays & promotions.  
✔ **Dynamic Pricing Strategies** → Adjust prices based on demand forecasts.  
✔ **Marketing Campaigns** → Target promotions around high-sales periods.  
✔ **Regional Planning** → Customize inventory for different store clusters.  

---

## 🚀 How to Run the Project
### **1️⃣ Clone the Repository**
```bash
git clone https://github.com/your-username/sales-forecasting.git
cd sales-forecasting
