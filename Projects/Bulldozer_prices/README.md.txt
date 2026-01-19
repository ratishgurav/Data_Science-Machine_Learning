# 🚜 Bulldozer Price Prediction

> **Goal:** Predict the future sale price of a bulldozer, given its characteristics and previous examples of how much similar bulldozers have been sold for.

## 📌 Overview
This project is a **Time-Series Regression** problem. We are using data from the past (sales from 1989 to 2012) to predict the future auction prices of heavy industrial equipment.

The dataset comes from the [Kaggle Bluebook for Bulldozers competition](https://www.kaggle.com/c/bluebook-for-bulldozers/data).

## 📂 Data Description (Asset Info)
The data is split into three parts:
* **Train.csv:** Training set, which contains data through the end of 2011.
* **Valid.csv:** Validation set, which contains data from January 1, 2012 - April 30, 2012.
* **Test.csv:** Test set, which contains data from May 1, 2012 - November 2012.

### 🔑 Key Features
The dataset contains over 50 features. The most critical ones used in the model include:

| Feature Name | Description |
| :--- | :--- |
| `SalesID` | Unique identifier of the sale. |
| `MachineID` | Unique identifier of the machine. |
| `saledate` | The date of the sale (Critical for Time Series). |
| `Saleprice` | **(Target Variable)** The price the machine sold for. |
| `YearMade` | The year the machine was manufactured. |
| `ModelID` | Unique identifier for the machine model. |
| `datasource` | The source of the sale record. |
| `auctioneerID` | Identifier of the entity that sold the machine. |
| `UsageBand` | Low, Medium, or High usage tier. |
| `fiModelDesc` | Description of the model configuration. |

*(Note: The full Data Dictionary is available in `Data Dictionary.xlsx` provided by Kaggle.)*

## 📊 Evaluation Metric
Since this is a regression problem, the competition evaluation metric is **RMSLE (Root Mean Squared Log Error)**.
* We focus on the *ratio* between predictions and actual values rather than the absolute difference.
* **Goal:** Minimize RMSLE.

## 🛠️ Tech Stack & Methodology
* **Python:** Core programming language.
* **Pandas & NumPy:** For data manipulation and structure.
* **Matplotlib & Seaborn:** For Exploratory Data Analysis (EDA) and visualization.
* **Scikit-Learn:** For modeling (RandomForestRegressor) and evaluation.

### Key Steps in Notebook:
1.  **Data Loading:** Parsing dates correctly using `parse_dates`.
2.  **Feature Engineering:** Extracting Year, Month, Day, and DayOfWeek from `saledate`.
3.  **Handling Missing Data:** Filling numeric missing values with median; filling categorical missing values with codes.
4.  **Encoding:** Converting string/object columns into Categories.
5.  **Modeling:** Training a `RandomForestRegressor`.
6.  **Hyperparameter Tuning:** Using `RandomizedSearchCV` to optimize the model.

## 📈 Results
* **Training RMSLE:** [Insert your score, e.g., 0.14]
* **Valid RMSLE:** [Insert your score, e.g., 0.25]
* **Feature Importance:** The model found `YearMade` and `ProductSize` to be the most indicative of price.

## 🚀 How to Run
1.  **Clone this repo.**
2.  **Download the Data:**
    * Due to file size limits, the data is not included in this repo.
    * Download `Train.csv` and `Valid.csv` from [Kaggle](https://www.kaggle.com/c/bluebook-for-bulldozers/data).
    * Place them in the `data/` folder.
3.  **Run the Notebook:**
    ```bash
    jupyter notebook Bulldozer_price_prediction.ipynb
    ```

---

## 🔗 Links
* [**View Notebook on Kaggle**](https://www.kaggle.com/code/ratishgurav/bulldozer-price-prediction) 