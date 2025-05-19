# 📊 IQR Method for Outlier Detection – Machine Learning Notes

## 🔍 What is IQR?

The **Interquartile Range (IQR)** is a measure of statistical dispersion and variability. It represents the range between the **first quartile (Q1)** and **third quartile (Q3)** in a dataset.

- **Q1 (25th percentile):** Median of the lower half of the data
- **Q3 (75th percentile):** Median of the upper half of the data
- **IQR = Q3 - Q1**

---

## ⚠️ Why Use IQR for Outlier Detection?

The IQR method is effective because it focuses on the **middle 50% of the data** and ignores extreme values. It works well with **non-normally distributed data** and is **robust to skewed distributions**.

---

## 🧮 IQR Formula

```text
IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR
```

- Data points **below the lower bound** or **above the upper bound** are considered **outliers**.

---

## 🛠️ Step-by-Step Implementation (Python)

```python
import pandas as pd

# Sample data
data = {'value': [10, 12, 12, 13, 14, 15, 100, 110]}
df = pd.DataFrame(data)

# Calculate Q1, Q3, and IQR
Q1 = df['value'].quantile(0.25)
Q3 = df['value'].quantile(0.75)
IQR = Q3 - Q1

# Define bounds
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

# Detect outliers
outliers = df[(df['value'] < lower_bound) | (df['value'] > upper_bound)]
print("Outliers:\n", outliers)

# Optional: Remove outliers
df_filtered = df[(df['value'] >= lower_bound) & (df['value'] <= upper_bound)]
```

---

## 📌 Pros of IQR Method

- ✅ Simple and interpretable
- ✅ Non-parametric (no assumptions about distribution)
- ✅ Robust to outliers and skewed data

---

## ❌ Cons of IQR Method

- ❌ May not work well with small datasets
- ❌ Threshold (1.5×IQR) is arbitrary; can be adjusted based on domain

---

## 💡 Tips

- Use **visualizations** like boxplots to see IQR and outliers visually:
  
```python
import seaborn as sns
sns.boxplot(x=df['value'])
```

- For **multivariate outlier detection**, combine IQR with PCA or model-based methods.

---

## 📚 Use Cases in ML

- Data preprocessing and cleaning
- Outlier handling in regression/classification tasks
- Robust feature engineering

---

## 🔁 Alternative Thresholds (Optional)

You can modify the multiplier (1.5) to make detection stricter or looser:

| Multiplier | Sensitivity |
|------------|-------------|
| 1.0        | High        |
| 1.5        | Standard    |
| 3.0        | Conservative|

---

## ✅ Summary

- **IQR** is a powerful tool for detecting outliers, especially in **non-normal datasets**.
- Outliers are points outside **[Q1 - 1.5*IQR, Q3 + 1.5*IQR]**
- Combine with **domain knowledge** and **visualizations** for best results.
