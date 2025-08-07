# 🛒 MerRec Purchase Intent Prediction Pipeline (PySpark)

This project uses the **Mercari MerRec dataset** from Hugging Face to build an end-to-end scalable data intelligence platform using PySpark. The goal is to **predict whether a user session will result in a purchase**, based on behavior data like product views and cart events.

---

## 🚀 Project Objective

> Build a scalable ML pipeline to predict customer purchase intent using PySpark, with the ability to process large-scale session data efficiently.

---

## 📦 Dataset

- **Source**: [Mercari MerRec Dataset](https://huggingface.co/datasets/mercari-us/merrec)
- **Size**: ~5M interactions across ~750K user sessions
- **Converted Format**: Saved as `merrec_train.csv` for Spark ingestion

---

## 🧱 Tech Stack

| Layer       | Tools Used                  |
|-------------|-----------------------------|
| Language    | Python                      |
| Processing  | Apache Spark (PySpark)      |
| ML Library  | MLlib                       |
| Dev Tools   | VS Code, Hugging Face       |
| Data Format | CSV                         |

---

## 🧩 Pipeline Components

### 1. Data Ingestion
- Load the pre-downloaded CSV with `spark.read.csv()`
- Inspect schema, handle nulls

### 2. Data Cleaning
- Drop rows with null product ID or event type
- Convert `event_time` string to timestamp

### 3. Feature Engineering
- Extract hour from timestamp
- Count views, cart additions, purchases per session
- Compute derived features like `distinct_products`

### 4. Label Creation
- Binary target: `purchase_intent` (1 if session contains purchase, else 0)

### 5. Machine Learning
- Vectorize features using `VectorAssembler`
- Train logistic regression model using `MLlib`
- Evaluate using AUC

### 6. Outputs
- Save model (`.save()`)
- Save predictions as CSV

---

## 📊 Model Features

| Feature Name        | Description                         |
|---------------------|-------------------------------------|
| `views`             | Number of products viewed           |
| `add_to_cart`       | Number of add-to-cart actions       |
| `distinct_products` | Unique products interacted within session |
| `purchase_intent`   | Target (0 = No purchase, 1 = Purchased) |

---

## 📈 Evaluation

| Metric | Value |
|--------|-------|
| AUC    | *0.85* (example) |

---

## 📂 Folder Structure

├── merrec_train.csv
├── merrec_pipeline.py
├── predictions.csv
├── purchase_intent_model/
├── README.md


---

## 💡 Future Work

- Add Random Forest, XGBoost models
- Use session length/time gap features
- Deploy with Streamlit frontend for real-time prediction

---


