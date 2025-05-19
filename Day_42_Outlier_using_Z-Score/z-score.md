# 📌 Z-Score in Machine Learning

## 🔍 What is Z-Score?
A **Z-score** (or **standard score**) tells you how many standard deviations a data point is from the **mean** of the distribution.

---

## 🧮 Z-Score Formula

\[
z = \frac{x - \mu}{\sigma}
\]

Where:
- **x**: the data point  
- **μ (mu)**: mean of the data  
- **σ (sigma)**: standard deviation of the data  
- **z**: resulting Z-score

---

## 🧠 Intuition

- `z = 0` → data point is exactly at the mean  
- `z = 2` → data point is 2 standard deviations above the mean  
- `z = -3` → data point is 3 standard deviations below the mean  

---

## 🎯 Why Use Z-Score in ML?

- **Outlier detection**  
  - Points with `|z| > 3` are considered outliers in a normal distribution  
- **Feature scaling** (used in standardization)  
- **Data normalization** for algorithms like:
  - Logistic Regression  
  - SVM  
  - KNN  
  - Neural Networks  

---

## 📊 When is Z-Score Effective?

- ✅ Works well when the data is **normally distributed**  
- ❌ Not suitable for **highly skewed data**  

---

## 🛠️ Z-Score for Outlier Detection (Python Example)

```python
import pandas as pd
import numpy as np
from scipy import stats

# Sample dataset
data = {'value': [10, 12, 12, 13, 12, 14, 100]}
df = pd.DataFrame(data)

# Calculate Z-score
df['z_score'] = np.abs(stats.zscore(df['value']))

# Filter out outliers
outliers = df[df['z_score'] > 3]
print("Outliers:\n", outliers)
```
## Tips
- Use absolute Z-score (np.abs) when checking both tails.
- Combine with visualizations (boxplot, histogram) for better understanding.
- For skewed data, prefer IQR or model-based methods (e.g., Isolation Forest).