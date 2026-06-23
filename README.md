# Score Prediction Analysis (성적 예측 분석)

> Analyze student performance factors and predict final exam scores using exploratory data analysis and linear regression. (학생 성적 영향 요인을 탐색하고 선형 회귀로 최종 시험 점수를 예측하는 분석 프로젝트)

---

## 🛠️ Tech Stack (기술 스택)

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-2.x-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557C)
![seaborn](https://img.shields.io/badge/seaborn-0.x-4C72B0)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?logo=scikitlearn&logoColor=white)

---

## ✨ Features (주요 기능)

- **Exploratory Data Analysis (탐색적 데이터 분석)**: distribution checks for numeric and categorical variables, missing value handling, outlier detection via boxplot and IQR
- **Correlation Analysis (상관관계 분석)**: heatmap of all numeric features vs `Exam_Score`, scatter plots with regression lines and Pearson r values
- **Feature Engineering (피처 엔지니어링)**: label encoding for categorical columns, ordinal mapping for `Parental_Involvement`, `Parental_Education_Level`, `Family_Income` into a composite `Parental_Impact_Score`; Korean 9-grade conversion for `Previous_Scores` and `Exam_Score`; binning of `Hours_Studied` and `Attendance`
- **Linear Regression Model (선형 회귀 모델)**: `StandardScaler` preprocessing + `LinearRegression` training, evaluation with RMSE and R²

---

## 📁 Project Structure (프로젝트 구조)

```text
score-prediction-analysis/
├── analysis.ipynb                  # Main analysis notebook (분석 메인 노트북)
├── StudentPerformanceFactors.csv   # Source dataset (원본 데이터셋)
└── README.md
```

---

## 🔄 Usage Flow (사용 흐름)

```
Raw CSV
  └─► Data Loading & Shape Check
        └─► Missing Value & Outlier Handling
              └─► EDA (Distribution / Correlation / Visualization)
                    └─► Feature Engineering (Encoding / Binning / Composite Score)
                          └─► Train-Test Split (80:20)
                                └─► StandardScaler → LinearRegression
                                      └─► Evaluation (RMSE, R²)
```

---

## 🏗️ Architecture (아키텍처)

### Dataset (데이터셋)

| Item | Detail |
|------|--------|
| Source | [Kaggle – Student Performance Factors](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors/data) |
| Rows | 6,607 |
| Columns | 20 |
| Target | `Exam_Score` |

**Numeric features (수치형):** `Hours_Studied`, `Attendance`, `Sleep_Hours`, `Previous_Scores`, `Tutoring_Sessions`, `Physical_Activity`

**Categorical features (범주형):** `Parental_Involvement`, `Access_to_Resources`, `Extracurricular_Activities`, `Motivation_Level`, `Internet_Access`, `Family_Income`, `Teacher_Quality`, `School_Type`, `Peer_Influence`, `Learning_Disabilities`, `Parental_Education_Level`, `Distance_from_Home`, `Gender`

### Model Pipeline (학습 파이프라인)

```
Numeric features (6)
        │
        ▼
StandardScaler
        │
        ▼
LinearRegression
        │
        ▼
  Exam_Score (predicted)
```

- Split: `train_test_split(test_size=0.2, random_state=42)`
- Scaler: `StandardScaler` (fit on train, transform on test)
- Model: `sklearn.linear_model.LinearRegression`
- Metrics: **RMSE** (mean absolute error in score units), **R²** (coefficient of determination)

### Key Findings (핵심 분석 결과)

| Correlation Strength | Features |
|---------------------|----------|
| Strong (강한 상관) | `Attendance` |
| Moderate (중간 상관) | `Hours_Studied` |
| Weak (약한 상관) | `Previous_Scores`, `Tutoring_Sessions` |
| Negligible (무시 수준) | `Motivation_Level` (r ≈ 0.08) |

- External environment features (`Access_to_Resources`, `Internet_Access`, `Teacher_Quality`, etc.) each show correlations below 0.2 individually, suggesting composite influence rather than single-factor effect. (외부 환경 변수들은 개별 상관관계가 0.2 미만으로, 복합적인 영향을 시사)
- `Exam_Score` values above 100 were capped to 100 (data quality correction). (`Exam_Score` 101 이상 값은 100으로 보정 처리)

---

## ⚙️ Environment Setup (환경 설정)

**Requirements (의존 패키지):**

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

**Conda environment (콘다 환경):**

```bash
conda create -n score-pred python=3.12
conda activate score-pred
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

> The notebook was developed in a `Malgun Gothic` font environment on Windows for Korean labels. On non-Windows systems, replace `plt.rc('font', family='Malgun Gothic')` with a locally available Korean font or `NanumGothic`.

---

## 🚀 How to Run (실행 방법)

```bash
git clone https://github.com/vosnuev/score-prediction-analysis.git
cd score-prediction-analysis
jupyter notebook analysis.ipynb
```

Run all cells in order from top to bottom. (셀을 위에서 아래로 순서대로 실행)

---

## 📄 License & References (라이선스 & 참고 문서)

- Dataset: [Kaggle – Student Performance Factors](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors/data) (CC BY 4.0)
- [scikit-learn LinearRegression docs](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
- [seaborn documentation](https://seaborn.pydata.org/)
