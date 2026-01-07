# Student Exam Score Predictor

## Problem Description
This project addresses the challenge of predicting student academic performance based on their daily habits and background. In educational settings, identifying students who might struggle early in the semester allows teachers to provide extra support.

The goal of this project is to build a machine learning model that predicts a student's final exam score based on features like **study hours, sleep hours, previous scores, and extracurricular activities**. The solution is a web service (built with Streamlit) where a user can input student data and get an instant score prediction. This service is containerized using Docker to ensure it runs consistently across any environment.

---

## Exploratory Data Analysis (EDA)
In the `notebook.ipynb`, I performed an extensive EDA to understand the dataset:

* **Basic Statistics:** Checked min, max, mean, and standard deviation for all numerical features.
* **Missing Values:** Confirmed the dataset had no missing values.
* **Target Variable Analysis:** Analyzed the distribution of 'Exam_Score' to ensure it follows a normal distribution.
* **Correlation & Feature Importance:** Used a correlation matrix to see which habits (like study hours) have the strongest impact on the final score.



---

## Model Training and Tuning
I experimented with multiple models to find the best performer:

* **Linear Regression:** Used as a baseline model.
* **Decision Tree Regressor:** Tested for capturing non-linear relationships.
* **Random Forest Regressor:** A tree-based ensemble method.

**Hyperparameter Tuning:** I used `GridSearchCV` to tune the Random Forest model, adjusting the number of estimators (`n_estimators`) and the depth of the trees (`max_depth`) to achieve the lowest Mean Squared Error (MSE). The final model is saved as `best_model.pkl`.

---

## Dependency and Environment Management
To run this project, you should use a virtual environment.

1. **Create a virtual environment:**
   ```bash
   python -m venv venv

2. **Activate it:**
* **Windows:** `.\venv\Scripts\activate`
* **Mac/Linux:** `source venv/bin/activate`


3. **Install dependencies:**
```bash
pip install -r requirements.txt

```


---

## Reproducibility

To reproduce the results:

* Ensure the dataset `student_habits_performance.csv` is in the `Data` folder.
* Run the `notebook.ipynb` to see the full analysis and training process.
* Alternatively, you can run the exported training logic (if you have a standalone `train.py`).

---

## Model Deployment

The model is deployed using **Streamlit**.

* The `app.py` script loads the `best_model.pkl`.
* Users can input student data via a sidebar.
* The app displays the predicted score in real-time.

---

## Containerization

The application is fully containerized using **Docker**.

**To build the container:**

```bash
docker build -t my-streamlit-app .

```

**To run the container:**

```bash
docker run -p 8501:8501 my-streamlit-app

```
