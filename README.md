# medical_data_visualizer
This project is part of the **freeCodeCamp Data Analysis with Python Certification**. It involves analyzing and visualizing medical examination data using categorical plots and heatmaps to better understand health trends.

## 🧾 Project Objective

- Clean and preprocess patient medical data.
- Create a **categorical plot** to visualize features related to cardiovascular disease.
- Create a **heatmap** to show correlations among various health indicators.

## 🧰 Technologies Used

- Python 🐍
- Pandas 📊
- NumPy 🔢
- Seaborn 🎨
- Matplotlib 📉

## ⚙️ How It Works

### 1. Data Preparation

```python
df = pd.read_csv("medical_examination.csv")

# Add 'overweight' column using BMI
df['overweight'] = (df['weight'] / ((df['height'] / 100) ** 2))
df['overweight'] = df['overweight'].apply(lambda x: 1 if x > 25 else 0)

# Normalize 'cholesterol' and 'gluc' (1 = good, >1 = bad → convert to binary)
df['cholesterol'] = df['cholesterol'].apply(lambda x: 1 if x > 1 else 0)
df['gluc'] = df['gluc'].apply(lambda x: 1 if x > 1 else 0)
2. Categorical Plot (draw_cat_plot())
Transforms the data using pd.melt().

Groups it by features like cholesterol, gluc, smoke, alco, active, and overweight.

Displays counts for each feature based on presence (value) and cardiovascular disease (cardio).

python
Copy
Edit
sns.catplot(
    data=df_cat_grouped,
    x='variable',
    y='total',
    hue='value',
    col='cardio',
    kind='bar'
)
3. Heatmap (draw_heat_map())
Filters out invalid data (like ap_lo > ap_hi or outliers).

Computes correlation matrix.

Displays a clean and annotated heatmap with upper triangle masked.

python
Copy
Edit
sns.heatmap(
    corr,
    mask=mask,
    annot=True,
    fmt=".1f",
    center=0,
    vmax=0.3,
    square=True,
    linewidths=0.5,
    cbar_kws={"shrink": 0.5}
)
📊 Outputs
Categorical Plot: Visualizes how different features are distributed among people with and without cardiovascular disease.

Heatmap: Displays correlation between health indicators like weight, cholesterol, glucose, blood pressure, and more.
