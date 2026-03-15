# 🫀 Heart Disease Prediction — End to End ML Project

A complete end-to-end machine learning project that predicts the likelihood of heart disease using the Cleveland Heart Disease dataset. Built with a FastAPI backend and Streamlit frontend.

---

## 📁 Project Structure

```
Heart Disease Prediction E2E/
├── data/
│   └── heart_cleveland_upload.csv   ← Cleveland dataset
├── model/
│   └── heart_disease_model.pkl      ← Trained model
├── notebook/
│   └── notebook.ipynb               ← EDA, training, evaluation
├── src/
│   ├── backend/
│   │   └── main.py                  ← FastAPI app
│   └── frontend/
│       └── app.py                   ← Streamlit dashboard
├── requirements.txt
└── README.md
```

---

## 🧠 ML Pipeline

- **Dataset:** Cleveland Heart Disease Dataset (303 samples, 13 features)
- **Models Compared:** Logistic Regression, Random Forest, XGBoost
- **Best Model:** XGBoost (selected based on Recall — minimizing false negatives)
- **Threshold Tuning:** Optimized for recall to reduce missed diagnoses
- **Serialization:** `joblib`

---

## ⚙️ Backend — FastAPI

- `POST /predict` — Takes patient details, returns prediction + probability
- `GET /health` — Check if model is loaded and API is running
- `GET /` — Welcome page with links

**Input features:**

| Feature | Description |
|---|---|
| age | Age of patient |
| sex | 0 = Female, 1 = Male |
| cp | Chest pain type (0–3) |
| trestbps | Resting blood pressure |
| chol | Serum cholesterol |
| fbs | Fasting blood sugar |
| restecg | Resting ECG results |
| thalach | Max heart rate achieved |
| exang | Exercise induced angina |
| oldpeak | ST depression |
| slope | Slope of peak exercise ST |
| ca | Major vessels colored (0–3) |
| thal | Thalassemia (0–3) |

---

## 🎨 Frontend — Streamlit

- Two column input form with labeled dropdowns
- Color coded prediction result (✅ / ❌)
- Disease probability metric

---

## 🚀 How to Run

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Start FastAPI backend
```bash
cd src/backend
uvicorn main:app --reload
```
API runs at: `http://127.0.0.1:8000`
Swagger docs: `http://127.0.0.1:8000/docs`

### 3. Start Streamlit frontend
```bash
cd src/frontend
streamlit run app.py
```
Dashboard runs at: `http://localhost:8501`

> ⚠️ Both terminals must be running at the same time.

---

## 📊 Sample Prediction

**Input:**
```json
{
  "age": 63, "sex": 1, "cp": 3,
  "trestbps": 145, "chol": 233,
  "fbs": 1, "restecg": 2,
  "thalach": 150, "exang": 0,
  "oldpeak": 2.3, "slope": 0,
  "ca": 0, "thal": 1
}
```

**Output:**
```json
{
  "heart_disease_prediction": 1,
  "disease_probability": 0.5998,
  "result": "Heart Disease Detected"
}
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| ML | scikit-learn, XGBoost |
| API | FastAPI, Pydantic |
| Dashboard | Streamlit |
| Data | Pandas, NumPy |
| Serialization | Joblib |

---

## 🔮 Planned Features

- [ ] SHAP explainability — feature impact per prediction
- [ ] Risk meter gauge chart
- [ ] Prediction history logging
- [ ] Docker containerization
- [ ] Cloud deployment (Render / Railway)

---

## 👤 Author

**Mohammad Naif** — Cool Data Science Undergrad Student  
