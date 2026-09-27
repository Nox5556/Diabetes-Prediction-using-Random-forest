🩺 Diabetes Prediction Using Random Forest

A Machine Learning project that predicts diabetes using the Random Forest Classification algorithm, with GridSearchCV-based hyperparameter tuning to identify a better-performing model configuration.

«Note: This project is intended for educational and machine-learning demonstration purposes. It is not a medical diagnostic system.»

📌 Project Overview

This project applies supervised machine learning to the Pima Indians Diabetes Dataset to predict whether a patient is likely to have diabetes.

The workflow includes:

- Exploratory Data Analysis (EDA)
- Data preprocessing
- Train-test splitting
- Random Forest classification
- Hyperparameter tuning using GridSearchCV
- Model evaluation
- Feature importance analysis

---

🧠 Machine Learning Approach

Random Forest Classifier

Random Forest is an ensemble learning algorithm that combines multiple Decision Trees.

Each tree makes an individual prediction, and the final classification is determined by combining the predictions from all trees.

🔧 Hyperparameter Tuning with GridSearchCV

Instead of relying only on default Random Forest parameters, GridSearchCV is used to systematically test different combinations of hyperparameters.

For example:

from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import RandomForestClassifier

rf = RandomForestClassifier(random_state=42)

param_grid = {
    'n_estimators': [50, 100, 200],
    'max_depth': [None, 10, 20],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4]
}

grid_search = GridSearchCV(
    estimator=rf,
    param_grid=param_grid,
    cv=5,
    scoring='accuracy',
    n_jobs=-1
)

grid_search.fit(X_train, y_train)

Best Parameters

The best hyperparameters can be obtained using:

print(grid_search.best_params_)

The best model is then:

best_model = grid_search.best_estimator_

This tuned model is used for the final predictions.

---

🔄 Machine Learning Workflow

                 Dataset
                    ↓
            Data Exploration
                    ↓
            Data Preprocessing
                    ↓
             Train-Test Split
                    ↓
          Random Forest Classifier
                    ↓
              GridSearchCV
                    ↓
        Hyperparameter Optimization
                    ↓
             Best RF Model
                    ↓
               Prediction
                    ↓
             Model Evaluation
                    ↓
          Feature Importance

---

📊 Dataset

The project uses the Pima Indians Diabetes Dataset.

Features

Feature| Description
"Pregnancies"| Number of pregnancies
"Glucose"| Plasma glucose concentration
"BloodPressure"| Diastolic blood pressure
"SkinThickness"| Triceps skin-fold thickness
"Insulin"| 2-Hour serum insulin
"BMI"| Body Mass Index
"DiabetesPedigreeFunction"| Diabetes pedigree function
"Age"| Age of the patient
"Outcome"| Target variable: 0 = No Diabetes, 1 = Diabetes

---

📈 Model Evaluation

After obtaining the best Random Forest model through GridSearchCV:

y_pred = best_model.predict(X_test)

Accuracy

from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)

print("Test Accuracy:", accuracy)

Classification Report

from sklearn.metrics import classification_report

print(classification_report(y_test, y_pred))

The classification report provides:

- Precision
- Recall
- F1-score
- Support

Confusion Matrix

from sklearn.metrics import confusion_matrix
import seaborn as sns
import matplotlib.pyplot as plt

cm = confusion_matrix(y_test, y_pred)

sns.heatmap(cm, annot=True, fmt="d")

plt.xlabel("Predicted")
plt.ylabel("Actual")
plt.title("Confusion Matrix")

plt.show()

---

🌳 Feature Importance

The optimized Random Forest model can also be used to determine feature importance.

importance = pd.Series(
    best_model.feature_importances_,
    index=X.columns
).sort_values(ascending=False)

importance.plot(kind="bar")

plt.title("Feature Importance")
plt.xlabel("Features")
plt.ylabel("Importance")

plt.show()

This provides an indication of which features the trained model relied on most for its predictions.

---

📊 Results

Add the actual results obtained from your notebook here:

Model: Random Forest Classifier

Hyperparameter Tuning: GridSearchCV
Cross-Validation: 5-Fold

Best Parameters:
{Add your best parameters here}

Test Accuracy:
XX.XX%

Precision:
XX.XX%

Recall:
XX.XX%

F1-Score:
XX.XX%

Do not use assumed accuracy values. Replace these with the actual results from your notebook.

---

🛠️ Technologies Used

- Python
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

Important Scikit-learn Components

train_test_split
RandomForestClassifier
GridSearchCV
accuracy_score
classification_report
confusion_matrix

---

📂 Project Structure

Diabetes-Prediction/
│
├── diabetes_prediction.ipynb
├── diabetes.csv
├── README.md
└── requirements.txt

---

🚀 Installation

Clone the repository:

git clone https://github.com/your-username/Diabetes-Prediction.git

Navigate into the project:

cd Diabetes-Prediction

Install dependencies:

pip install -r requirements.txt

Launch Jupyter Notebook:

jupyter notebook

Then open:

diabetes_prediction.ipynb

---

💡 Key Learning Outcomes

This project demonstrates:

- Exploratory Data Analysis
- Data preprocessing
- Supervised machine learning
- Binary classification
- Random Forest
- Hyperparameter optimization
- Cross-validation
- GridSearchCV
- Model evaluation
- Confusion matrix analysis
- Feature importance
- Model prediction

---

🔮 Future Improvements

Possible improvements include:

- Comparing Random Forest with Logistic Regression, SVM and XGBoost.
- Trying "RandomizedSearchCV" for larger hyperparameter spaces.
- Using Stratified K-Fold Cross-Validation.
- Applying techniques to handle class imbalance.
- Adding SHAP for model explainability.
- Creating an interactive Streamlit application.
- Deploying the trained model as an API.

---

⚠️ Disclaimer

This project is intended for educational and research purposes only. The model's predictions should not be considered a medical diagnosis or medical advice. Medical decisions should be made by qualified healthcare professionals.

---

👨‍💻 Author

Siddhesh Bagul

Electronics Engineering Student
Walchand College of Engineering, Sangli
