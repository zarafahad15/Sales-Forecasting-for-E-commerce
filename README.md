# Sales-Forecasting-for-E-commerce
> End-to-end ML pipeline for predicting future e-commerce sales using historical order data, marketing spend, and seasonal features.  
> Built with *Python, **XGBoost, and **Flask* — designed for real-time business insights and decision-making.

---

## 🚀 Project Overview

This project forecasts *daily/weekly sales* for an e-commerce store based on:

- Historical sales data  
- Marketing & discount campaigns  
- Holidays & seasonal patterns  
- Customer traffic and conversion trends  

The model provides *short-term sales predictions* that help optimize inventory, logistics, and ad spend — a common real-world ML use case in retail analytics.

✅ *Goal:* Build a deployable ML system for sales forecasting.  
✅ *Use Case:* Demand forecasting, inventory management, dynamic pricing.  
✅ *Skills Demonstrated:* Data preprocessing, feature engineering, model tuning, interpretability, and ML deployment.

---

## 🧰 Tech Stack

| Category | Tools / Libraries |
|-----------|-------------------|
| *Languages* | Python 3.10+ |
| *Data Handling* | Pandas, NumPy |
| *Modeling* | XGBoost, Scikit-learn |
| *Visualization* | Matplotlib, SHAP |
| *Serving / API* | Flask |
| *Environment* | virtualenv / pip |

---

## 📂 Repository Structure

.
├── data_generation.py       # Creates synthetic e-commerce sales data
├── train_model.py           # Trains and evaluates sales forecasting model
├── app.py                   # Flask REST API for prediction
├── requirements.txt          # Python dependencies
├── shap_summary.png          # Model interpretability plot (auto-generated)
└── README.md                 # You are here

---

## 🧪 Features & Workflow

1. *Data Generation / Ingestion*
   - Generates synthetic e-commerce sales data: product category, price, ads spend, discounts, and daily sales.  
   - Replaceable with real sales data from Shopify, Amazon, or custom APIs.

2. *Feature Engineering*
   - Date-based features: day, week, month, weekday, holiday flag  
   - Marketing and discount interactions  
   - Rolling sales averages and lag features for temporal patterns  
   - Encoded categorical features (category, region, etc.)

3. *Model Training*
   - Uses *XGBoostRegressor* with grid search optimization  
   - Validated using time-based cross-validation  
   - Evaluation metrics: *MAE, **RMSE, **MAPE*  
   - Includes SHAP explainability to understand key drivers (e.g., discount %, ad spend)

4. *Model Serving*
   - Flask API endpoint /predict for real-time predictions  
   - Accepts JSON input with recent sales, marketing, and date features  
   - Returns next-day or next-week forecasted sales

---

## 🧾 Example Input / Output

*Request*
```bash
curl -X POST http://127.0.0.1:5000/predict \
-H "Content-Type: application/json" \
-d '{
  "date":"2025-01-10",
  "category":"electronics",
  "price":59.99,
  "discount":10,
  "ad_spend":200,
  "traffic":1800,
  "sales_lag1":520,
  "sales_lag7":480,
  "sales_roll_mean_7":510.3,
  "is_holiday":0
}'

Response

{"prediction": 543.27}


⸻

⚙ How to Run Locally

1️⃣ Create environment and install dependencies

python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
pip install -r requirements.txt

2️⃣ Generate dataset

python data_generation.py --out data.csv --days 365

3️⃣ Train model

python train_model.py --data data.csv --model-path model.pkl

4️⃣ Run Flask API

python app.py --model-path model.pkl


⸻

📈 Model Evaluation

Metric	Description	Result (Example)
MAE	Mean Absolute Error	~42.3
RMSE	Root Mean Square Error	~61.5
MAPE	Mean Absolute Percentage Error	~7.8%
Top Features	ad_spend, discount, sales_lag1, is_holiday	


⸻

💡 Key Highlights for Recruiters
	•	🧩 Full end-to-end pipeline: raw data → training → evaluation → deployment
	•	⏳ Time-series forecasting using XGBoost + engineered lags & rolling features
	•	📊 Explainable AI (SHAP) for model transparency
	•	⚙ Production-grade API endpoint for inference
	•	🏬 Real-world relevance: demand forecasting, marketing ROI, and pricing optimization
	•	🧱 Clean repo structure and reproducible workflow for enterprise use

⸻

🧭 Next Improvements
	•	Add Streamlit dashboard for visualizing sales trends and predictions
	•	Integrate Facebook Prophet or LSTM for long-horizon forecasting
	•	Include real holiday & promo calendars
	•	Containerize using Docker and deploy on AWS / Render / GCP
------------------------------------------------------------------------
