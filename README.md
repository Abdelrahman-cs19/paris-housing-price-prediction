# Paris Housing Price Prediction 🏡

This project focuses on predicting housing prices in Paris using a dataset of **10,000 properties** with **17 structural and geographical features**. Various regression models were implemented, evaluated, and compared to identify the best model for accurately estimating house prices.

---

## 📌 Problem Statement

Predicting real estate prices is a classic regression problem influenced by multiple continuous and categorical features (e.g., square meters, number of rooms, presence of amenities like pools or yards, building year, etc.). 

The goal of this project is to:
1. Conduct Exploratory Data Analysis (EDA) and detect univariate/multivariate outliers.
2. Build and compare multiple machine learning regression algorithms.
3. Determine the best-performing model based on $R^2$ Score and Root Mean Squared Error (RMSE).

---

## 📊 Dataset Details

- **Dataset Name:** `ParisHousing.csv`
- **Total Records:** 10,000 rows
- **Total Features:** 17 (16 predictor features + 1 target variable `price`)
- **Missing Values:** None (0 null values across all columns)

### Features Description:
| Feature Name | Data Type | Description |
| :--- | :--- | :--- |
| `squareMeters` | Numeric (int) | Total area of the property in square meters |
| `numberOfRooms` | Numeric (int) | Number of rooms in the property |
| `hasYard` | Binary (0/1) | Whether the property has a yard |
| `hasPool` | Binary (0/1) | Whether the property has a swimming pool |
| `floors` | Numeric (int) | Number of floors |
| `cityCode` | Numeric (int) | Zip/City code of the property location |
| `cityPartRange` | Numeric (int) | Range index of the city part (location quality) |
| `numPrevOwners` | Numeric (int) | Number of previous owners |
| `made` | Numeric (int) | Year the property was built |
| `isNewBuilt` | Binary (0/1) | Whether the building is newly constructed |
| `hasStormProtector` | Binary (0/1) | Presence of storm protection |
| `basement` | Numeric (int) | Basement area size |
| `attic` | Numeric (int) | Attic area size |
| `garage` | Numeric (int) | Garage size |
| `hasStorageRoom` | Binary (0/1) | Presence of storage room |
| `hasGuestRoom` | Numeric (int) | Number/Presence of guest rooms |
| `price` **(Target)** | Continuous (float) | Price of the property (Target variable) |

---

## 🛠️ Data Preprocessing & Outlier Analysis

### 1. Data Cleaning
- Verified missing values: **0 nulls found** across the dataset.
- Data types converted and validated to numeric formats.

### 2. Outlier Detection Methods
- **Univariate Outlier Detection:**
  - **Z-Score Method ($|z| > 3$):** 0 outliers detected across key numerical columns (`price`, `squareMeters`, `numberOfRooms`, `floors`, `made`, etc.).
  - **IQR Rule ($1.5 \times IQR$):** 0 univariate outliers detected.
- **Multivariate Outlier Detection:**
  - **Isolation Forest ($contamination = 0.01$):** Identified 100 potential multivariate anomalies.
  - **Local Outlier Factor (LOF, $k=20, contamination = 0.01$):** Identified 100 potential multivariate anomalies (e.g., indices 3180, 6443, 6249, etc.).

---

## 🤖 Models Used & Evaluation Pipeline

The project evaluates a wide range of regression algorithms:
1. **Linear Models:** Linear Regression, Ridge Regression, Lasso, ElasticNet
2. **Instance-Based Models:** K-Nearest Neighbors (KNN) Regressor
3. **Tree-Based & Ensemble Models:** Random Forest Regressor, Extra Trees Regressor, Gradient Boosting Regressor
4. **Support Vector Machines:** Support Vector Regressor (SVR)

### Evaluation Metrics:
- **$R^2$ Score (Coefficient of Determination):** Measures how well the model explains the variance of the target variable.
- **Root Mean Squared Error (RMSE):** Measures the average magnitude of prediction errors in price units.

---

## 📈 Model Performance & Results

Given the near-linear relationship between `squareMeters` and `price` in the Paris Housing dataset:
- **Linear Regression & Ridge Regression** achieve exceptional performance with near-perfect fit ($R^2 \approx 0.99999$).
- **Random Forest & Gradient Boosting** provide very strong non-linear baseline fits ($R^2 > 0.98$).

| Model | $R^2$ Score | Performance Summary |
| :--- | :---: | :--- |
| **Linear Regression** | **0.99999** | **Best Model** — Near-zero residual error |
| **Ridge Regression** | **0.99999** | Top Performer with L2 Regularization |
| **Lasso Regression** | ~0.9999 | Excellent accuracy |
| **Extra Trees Regressor** | ~0.99 | Highly accurate ensemble model |
| **Random Forest Regressor** | ~0.98 - 0.99 | Robust ensemble baseline |
| **Gradient Boosting Regressor** | ~0.98 | Strong tree-boosting performance |
| **KNN Regressor** | ~0.75 - 0.85 | Sensitive to feature scaling/distance metrics |
| **Support Vector Regressor (SVR)** | Variable | Dependent on kernel selection |

### 🏆 Best Model Selection
- **Winner:** **Linear Regression / Ridge Regression**
- **Reason:** Housing price in this synthetic/semi-synthetic Paris housing dataset correlates almost directly to square meters modified linearly by property attributes, making Linear Regression the most precise and computationally efficient model.

---

## 🚀 How to Run the Notebook

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/paris-housing-prediction.git
   cd paris-housing-prediction
   ```

2. **Install Dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

3. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

4. **Run Notebook:**
   Open `ParisHousing.ipynb` and run all cells sequentially.

---

## 📁 Repository Structure

```
├── ParisHousing.csv          # Housing dataset (10,000 samples)
├── ParisHousing.ipynb        # Data preprocessing, outlier analysis, and modeling notebook
└── README.md                 # Project documentation
```
