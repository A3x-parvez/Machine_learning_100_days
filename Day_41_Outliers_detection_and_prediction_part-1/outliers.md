# 📌 Outliers in Machine Learning – Cheat Sheet

## 🔍 What is an Outlier?
An outlier is a data point that differs significantly from other observations. It may be unusually high or low compared to the majority of the data.

## 🎯 Why Outliers Matter in ML
- Skew model performance (e.g., linear regression)
- Bias summary statistics (mean, standard deviation)
- Impact clustering & distance-based models (e.g., KNN, K-means)

## 📊 Common Causes of Outliers
- Measurement or entry errors
- Natural variability
- Experimental errors
- Fraudulent activities
- Novel/rare phenomena

## 🔎 How to Detect Outliers

### 1. Statistical Methods

**Z-score (Standard Score)**  
Formula: `z = (x - mean) / std_dev`  
Threshold: `|z| > 3` → outlier

**IQR (Interquartile Range) Method**  
```python
IQR = Q3 - Q1
Lower Bound = Q1 - 1.5*IQR
Upper Bound = Q3 + 1.5*IQR
# Values outside bounds are outliers

## 2. Visualization Techniques

- **Boxplot** → Quickly shows data spread and outliers  
- **Histogram** → Skewed bars may indicate outliers  
- **Scatter Plot** → Detects outliers in 2D space  
- **Pair Plot / Heatmap** → For multivariate analysis  

## 3. Model-Based Methods

- **Isolation Forest**  
- **One-Class SVM**  
- **DBSCAN clustering**  
- **Local Outlier Factor (LOF)**  

---

## 🛠️ How to Handle Outliers

### 1. Remove Outliers
When they are errors or irrelevant to analysis:

```python
df = df[(df['col'] >= lower_bound) & (df['col'] <= upper_bound)]

### 2. Cap/Floor Outliers (Winsorization)

Replace extreme values with upper/lower percentiles:

```python
import scipy.stats as stats
df['col'] = stats.mstats.winsorize(df['col'], limits=[0.05, 0.05])

### 3. Transform Data

Use log, square root, or Box-Cox to reduce impact:

```python
df['col'] = np.log1p(df['col'])

### 4. Impute with Mean/Median
Replace outliers with the column's median or mean.

### 5. Use Models Robust to Outliers
- Tree-based models (e.g., Random Forest, XGBoost)
- Robust Regression (e.g., RANSAC)

### 🧠 Tips for ML Practice
- Always visualize before removing data
- Use domain knowledge to justify removing/keeping outliers
- For unsupervised models (clustering), try isolation-based detection
- Use robust metrics like median & IQR instead of mean & std dev