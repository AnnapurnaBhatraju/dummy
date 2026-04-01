# A Hybrid Ensemble Learning Framework for Transparent Anaemia Risk Prediction

## Project Overview
Anaemia is a global health concern where a decrease in hemoglobin or red blood cells can lead to severe complications if not detected early. This project develops a robust machine learning framework to predict Anaemia risk using a **Hybrid Ensemble Learning** approach.

To address the "Black-Box" nature of AI, this model incorporates **Explainable AI (XAI)** tools like **SHAP** (SHapley Additive exPlanations) and **LIME** (Local Interpretable Model-agnostic Explanations). This ensures medical experts can understand the feature contributions (Hemoglobin, MCH, MCV, etc.) behind every prediction.

## Features
* **Multi-Algorithm Comparison:** Evaluates performance across three stages:
    * **Existing:** Decision Tree.
    * **Proposed:** Gradient Boosting.
    * **Extension (Hybrid):** A Voting Classifier combining **Random Forest** and **XGBoost** using a **Soft Voting** mechanism for high-confidence predictions.
* **Transparent Diagnosis:** Provides local explanations for each patient, highlighting exactly which blood parameter increased or decreased the probability of Anaemia.
* **Web Dashboard:** A modern, interactive interface built with **Flask** and **React components** for data visualization and real-time prediction.
* **Automated Reporting:** Sends prediction results and confidence scores directly to the user's email.

## Tech Stack
* **Backend:** Flask (Python)
* **Frontend:** React.js, Tailwind CSS, Bootstrap, Vanta.js (Animations)
* **Machine Learning:** Scikit-Learn, XGBoost
* **Explainable AI:** SHAP, LIME
* **Database:** SQLite3

## Project Structure
```text
├── admin/               # Admin dashboard and data management
├── Dataset/             # Clinical data (anemia.csv)
├── model/               # Serialized ML models and data pickles
├── static/              # CSS, React components, and JS animations
├── templates/           # HTML templates (Flask/Jinja2)
├── utils/               # Core logic: algorithms, XAI, and email utilities
├── app.py               # Main Flask application entry point
├── signup.db            # SQLite database for user management
└── requirements.txt     # Python dependencies
```

## Dataset Parameters
The model analyzes the following clinical features to predict the **Result** (Anaemic / Not Anaemic). The dataset utilized for this research is the **Anaemia Prediction** dataset by Biswaranjan Rao, sourced from Kaggle.

* **Gender:** (0: Male, 1: Female)
* **Hemoglobin:** The protein in red blood cells that carries oxygen.
* **MCH (Mean Corpuscular Hemoglobin):** The average amount of hemoglobin per red blood cell.
* **MCHC (Mean Corpuscular Hemoglobin Concentration):** The average concentration of hemoglobin in a given volume of red blood cells.
* **MCV (Mean Corpuscular Volume):** The average size of your red blood cells.

> **Data Source:** https://www.kaggle.com/datasets/biswaranjanrao/anemia-dataset

## Explainable AI (XAI)
To ensure the framework is "transparent," we utilize two primary XAI techniques:
1. **SHAP (SHapley Additive exPlanations):** Assigns each feature an importance value for a particular prediction, showing how much each blood parameter contributed to the final risk score.
2. **LIME (Local Interpretable Model-agnostic Explanations):** Creates a local surrogate model to explain individual instances, making the AI's "thought process" understandable for healthcare professionals.

## Model Performance
The performance of the models was evaluated using standard metrics including Accuracy, Precision, and Recall. The results indicate that the **Extension (Hybrid Voting Classifier)** significantly outperforms standalone models.

| Model | Accuracy | Precision | Recall |
| :--- | :--- | :--- | :--- |
| Decision Tree (Existing) | 88.42% | 0.87 | 0.88 |
| Gradient Boosting (Proposed) | 94.15% | 0.93 | 0.94 |
| **Hybrid Voting Classifier (Extension)** | **97.63%** | **0.97** | **0.98** |

## Automated Notification & Reporting
The system is integrated with an **SMTP Email Service** to ensure seamless communication of results. Once the prediction is generated:
* The user receives a detailed email containing their anaemia status and confidence.
* The email clearly states the predicted risk status (**Anaemic** or **Not Anaemic**).
* It includes the model's confidence score and XAI-driven insights to ensure the user is well-informed about the prediction's basis.

## Installation & Setup

1. Clone the repo:
```bash
git clone https://github.com/AnnapurnaBhatraju/Anaemia-Prediction-XAI.git
cd Anaemia-Prediction-XAI
```

2. Install Dependencies:
```bash
pip install -r requirements.txt
```

3. Run the App:
```bash
python app.py
```

The application will be available at http://localhost:5000

## Contributing
1. Fork the Project.
2. Create your Feature Branch.
3. Commit your Changes.
4. Push to the Branch.
5. Open a Pull Request.

---
Developed by Annapurna Bhatraju

