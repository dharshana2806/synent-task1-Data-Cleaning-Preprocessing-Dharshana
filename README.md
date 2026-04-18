# 🚢 Titanic Data Cleaning & Preprocessing
### Task 1 – Data Cleaning | Synent Internship

---

## 📌 Problem Statement
Real-world data is always messy. Before any analysis or machine learning, we must clean and preprocess it. This project takes the raw Titanic passenger dataset and transforms it into a clean, structured, ML-ready format — handling missing values, removing duplicates, converting data types, and renaming columns.

---

## 📊 Dataset
- **Source:** [Titanic Dataset – DataScienceDojo](https://github.com/datasciencedojo/datasets/blob/master/titanic.csv)
- **Rows:** 891 passengers
- **Columns:** 12 features (PassengerId, Survived, Pclass, Name, Sex, Age, SibSp, Parch, Ticket, Fare, Cabin, Embarked)

---

## 🔧 Steps Performed

### 1. Load & Explore the Data
- Used `df.info()` to check column types and non-null counts
- Used `df.describe()` to get statistical summary

### 2. Check Missing Values
| Column | Missing Count | Missing % |
|--------|--------------|-----------|
| Cabin | 687 | 77.1% |
| Age | 177 | 19.9% |
| Embarked | 2 | 0.2% |

### 3. Handle Missing Values
| Column | Strategy | Reason |
|--------|----------|--------|
| `Cabin` | **Dropped** | 77% missing → not usable |
| `Age` | **Filled with median** | Median is robust to outliers |
| `Embarked` | **Filled with mode ('S')** | Only 2 missing; use most frequent |

### 4. Remove Duplicates
- Checked for duplicate rows → `df.drop_duplicates()`

### 5. Convert Data Types
| Column | Before | After |
|--------|--------|-------|
| `Sex` | `male/female` (text) | `0/1` (int) |
| `Embarked` | `S/C/Q` (text) | `0/1/2` (int) |
| `Age` | float | float (confirmed) |

### 6. Rename Columns
| Old Name | New Name |
|----------|----------|
| PassengerId | passenger_id |
| Pclass | passenger_class |
| SibSp | siblings_spouses |
| Parch | parents_children |
| (all others) | snake_case |

---

## 📈 Before vs After

| Metric | Before | After |
|--------|--------|-------|
| Rows | 891 | 891 |
| Columns | 12 | 11 |
| Missing Values | 866 | **0** |
| Duplicate Rows | 0 | 0 |
| Text Columns | Sex, Embarked, Cabin | None |
| Column naming | PascalCase | snake_case |

---

## 🛠️ Tools Used
- **Language:** Python 3
- **Libraries:** `pandas`, `numpy`
- **Environment:** Jupyter Notebook / Google Colab

---

## 📁 Project Files
```
synent-task1-datacleaning-yourname/
│
├── titanic.csv               ← Raw original dataset
├── cleaned_titanic.csv       ← Cleaned output dataset
├── Titanic_Data_Cleaning.ipynb  ← Full Jupyter Notebook with code + comments
└── README.md                 ← This file
```

---

## 🚀 How to Run
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/synent-task1-datacleaning-yourname.git
   ```
2. Open `Titanic_Data_Cleaning.ipynb` in Jupyter or Google Colab
3. Run all cells top to bottom
4. `cleaned_titanic.csv` will be generated automatically

---

## 💡 Key Observations
- **38%** of passengers survived (Survived mean = 0.38)
- **77%** of Cabin data was missing — dropped entirely
- **Age** ranged from 0.42 to 80 years; median = 28
- **Fare** ranged from 0 to £512; heavily right-skewed
- After cleaning: **zero missing values**, all numeric columns, consistent naming

---

*Made as part of Synent Data Science Internship – Task 1*
