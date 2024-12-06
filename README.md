# **Model Card: Titanic Survival Prediction**

## **Basic Information**
- **Person or organization developing model**: Himavarsha Yerrapothu (himavarsha.yerrapothu@gwu.edu), Rachel Aska Niharika (rachel.aska@gwu.edu).
- **Model Date**: December 6, 2024
- **Model Version**: 1.0
- **License**: MIT License
- **Model Implementation Code**: titanic-shipwreck-predicting-models-with-ml.ipynb

---

## **Intended Use**
- **Intended Uses**: 
  - Predict survival probability of Titanic passengers based on demographic and ticketing data.
  - Educational purposes and machine learning practice.
- **Intended Users**:
  - Students, educators, and beginner data scientists.
- **Out-of-Scope Uses**:
  - Applications requiring high-stakes decision-making.
  - Predictions outside the scope of the Titanic dataset.

---

## **Training Data**
- **Source**: [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic/data)
- **Data Splits**:
  - **Training Set**: 80% (712 rows)
  - **Validation Set**: 20% (179 rows)
- **Preprocessing**:
  - Missing values in `Age` and `Fare` were imputed using the median.
  - `Embarked` was filled with the most frequent value.
  - `Sex` and `Embarked` were encoded numerically.
- **Data Dictionary**:

| Name            | Modeling Role | Measurement Level | Description                                        |
|-----------------|---------------|-------------------|-----------------------------------------------     |
| **PassengerId** | ID            | int               | Unique row identifier                              |
| **Survived**    | Target        | int (binary)      | Survival status (1 = Survived, 0 = Did not survive)|
| **Pclass**      | Input         | int (ordinal)     | Passenger class (1 = 1st, 2 = 2nd, 3 = 3rd)        |
| **Name**        | Unused        | string            | Passenger name                                     |
| **Sex**         | Input         | int (binary)      | Gender (0 = Male, 1 = Female)                      |
| **Age**         | Input         | float             | Passenger's age (missing values imputed)           |
| **SibSp**       | Input         | int               | Number of siblings/spouses aboard                  |
| **Parch**       | Input         | int               | Number of parents/children aboard                  |
| **Fare**        | Input         | float             | Ticket fare                                        |
| **Embarked**    | Input         | int               | Port of embarkation (0 = C, 1 = Q, 2 = S)          |

---

## **Test Data**
- **Source**: [Kaggle Titanic Test Dataset](https://www.kaggle.com/c/titanic/data)
- **Number of Rows in Test Data**: 418
- **Differences in Columns**: No `Survived` column in the test set.

---

## **Model Details**
- **Input Features**: `Pclass`, `Sex`, `Age`, `SibSp`, `Parch`, `Fare`, `Embarked`
- **Target Variable**: `Survived`
- **Type of Models**: 
  - Logistic Regression
  - Decision Tree Classifier
  - Random Forest Classifier
- **Software**: Python, scikit-learn
- **Version**: Python 3.10, scikit-learn 1.3.0
- **Random Forest Hyperparameters**:
  ```python
  RandomForestClassifier(
      n_estimators=100,
      max_depth=5,
      random_state=1
  )


## **Quantitative Analysis**

### **Performance Metrics**

| Model                  | Dataset       | Accuracy | Precision | Recall | F1-Score |
|------------------------|---------------|----------|-----------|--------|----------|
| **Logistic Regression**| Training      | 80.0%    | 81.2%     | 78.4%  | 79.8%    |
|                        | Validation    | 78.0%    | 79.3%     | 75.9%  | 77.6%    |
| **Decision Tree**      | Training      | 97.9%    | 98.1%     | 97.6%  | 97.8%    |
|                        | Validation    | 79.0%    | 80.3%     | 76.5%  | 78.3%    |
| **Random Forest**      | Training      | 97.9%    | 98.2%     | 97.6%  | 97.9%    |
|                        | Validation    | 81.0%    | 82.4%     | 79.6%  | 81.0%    |

## **Conclusion**

### **Best Model: Random Forest Classifier**

The **Random Forest Classifier** is the best-performing model for the Titanic Survival Prediction project due to the following reasons:

1. **High Accuracy**: Achieved **97.9% training accuracy** and **81.0% validation accuracy**, demonstrating strong learning capability and good generalization.
2. **Balanced Performance**: Maintained a balance between **Precision** (82.4%) and **Recall** (79.6%), minimizing both false positives and false negatives.
3. **Feature Insights**: Identified key features influencing survival predictions, such as:
   - **Sex**
   - **Pclass**
   - **Fare**
   - **Age**
---

## **Ethical Considerations**

- **Bias**: The model relies heavily on features like **gender (Sex)** and **passenger class (Pclass)**, reflecting historical biases in survival rates.
- **Missing Data**: Imputation of missing values (e.g., **Age**, **Cabin**) may introduce inaccuracies.
- **Unbalanced Classes**: Unequal distribution of survivors and non-survivors could affect fairness in predictions.
- **Historical Context**: The dataset is specific to the 1912 Titanic disaster and not representative of modern scenarios.

