# EvLoads_pred

# ⚡ EV Charging Load Prediction

## 🚀 Project Overview
This project predicts **electric vehicle (EV) charging loads** based on historical **EV charging session data** and **local traffic distribution**. The goal is to forecast **energy demand** at charging stations, enabling better **grid management, infrastructure planning, and optimization of power distribution**.

---

## 📊 Dataset
We use two datasets:
1. **EV Charging Reports** (`EV charging reports.csv`)  
   - Contains session-wise EV charging information (energy consumed, duration, start/end times).
2. **Local Traffic Distribution** (`Local traffic distribution.csv`)  
   - Contains **traffic flow data**, which helps correlate road usage with EV charging patterns.

### 🔑 Key Features Used
| Feature | Description |
|---------|------------|
| `El_kWh` | Energy consumed in a charging session |
| `Power_kW` | Charging power level |
| `Session_duration` | Duration of charging session |
| `Traffic_density` | Local traffic levels (merged from traffic dataset) |
| `Weekday` | Day of the week |
| `Temperature` | Weather conditions affecting charging behavior |

---

## 🔄 Data Preprocessing
### 1️⃣ Merging Datasets
- The **EV Charging Reports** dataset is merged with the **Traffic Distribution** dataset using the `Start_plugin_hour` and `Date_from` columns.
  
### 2️⃣ Feature Selection
- We **drop unnecessary columns** such as session identifiers, timestamps, and categorical session data.

### 3️⃣ Data Cleaning
- Convert **string-based numeric values** (e.g., `"1,234"` → `"1.234"`).
- Convert all numeric columns to **float** format.

---

## 📉 Model Training
### 🛠 Train-Test Split
- The dataset is split into **80% training** and **20% testing**:
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y,
                                                    train_size=0.80,
                                                    test_size=0.20,
                                                    random_state=2)

