# ESG Prediction Dashboard

재무 및 비재무 데이터를 기반으로 기업의 차년도 ESG 등급을 예측하는 Streamlit 기반 머신러닝 대시보드입니다.

본 프로젝트는 ESG 등급 예측 문제를 회귀와 분류 관점에서 비교 분석하고, 최종적으로 XGBoost 기반 다중분류 모델을 활용하여 기업별 ESG 등급 예측 및 개선 전략을 제안하는 것을 목표로 합니다.

<br>

##  Demo

- Streamlit App: 배포 후 링크 입력
- GitHub Repository: 현재 저장소 링크 입력

<br>

##  Project Overview

ESG 평가는 기업의 지속가능성과 투자 매력도를 판단하는 중요한 지표입니다.  
본 프로젝트에서는 기업의 재무 지표와 일부 비재무 지표를 활용하여 차년도 ESG 등급을 예측하고, 예측 결과를 시각적으로 확인할 수 있는 대시보드를 구현했습니다.

주요 목표는 다음과 같습니다.

- 재무/비재무 지표 기반 ESG 등급 예측
- 회귀 모델과 분류 모델의 성능 비교
- XGBoost 기반 최종 예측 모델 구축
- SHAP 분석을 통한 예측 근거 해석
- 기업 검색 및 지표 시뮬레이션 기능 제공
- ESG 등급 개선을 위한 주요 변수 제안

<br>

##  Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Web App | Streamlit |
| Data Processing | Pandas, NumPy |
| Visualization | Plotly, Matplotlib |
| Machine Learning | Scikit-learn, XGBoost, LightGBM |
| Model Interpretation | SHAP |
| Model Save/Load | Joblib |

<br>

##  Main Features

### 1. ESG 등급 예측 대시보드

기업명 또는 종목코드를 검색하여 특정 연도의 ESG 등급을 확인하고, AI 모델의 예측 등급과 실제 등급을 비교할 수 있습니다.

### 2. 회귀 모델 분석

초기 회귀 모델의 설명력을 확인하고, 파생변수 추가 및 Rolling Window 분석을 통해 모델 성능 개선 과정을 시각화했습니다.

### 3. 분류 모델 분석

ESG 등급 예측 문제를 다중분류 문제로 재정의하고, Logistic Regression, Random Forest, SVM, LightGBM, XGBoost 모델의 성능을 비교했습니다.

### 4. 최종 모델 선정

최종 모델로 XGBoost 기반 분류 모델을 선정했습니다.  
과적합 가능성을 고려하여 max_depth 튜닝 결과를 비교하고, 일반화 성능을 기준으로 최종 모델을 선택했습니다.

### 5. SHAP 기반 모델 해석

SHAP 분석을 통해 각 변수가 ESG 등급 예측에 미치는 영향을 시각화했습니다.  
이를 통해 단순 예측 결과뿐 아니라, 모델이 어떤 근거로 등급을 판단했는지 확인할 수 있습니다.

### 6. Feature Simulation

사용자가 주요 지표 값을 직접 조정하면 ESG 예측 등급이 어떻게 변화하는지 확인할 수 있습니다.  
또한 목표 등급 상승을 위해 어떤 변수를 개선하면 좋을지 제안합니다.

<br>

##  Model Performance

| Stage | Metric | Score |
|---|---:|---:|
| Previous Research | R² Score | 0.225 |
| Initial Regression | R² Score | 0.440 |
| Advanced Regression | R² Score | 0.585 |
| Final Classification | ROC-AUC | 0.829 |

<br>

##  Project Structure

```text
esg-prediction-dashboard/
│
├─ app.py
├─ requirements.txt
├─ README.md
│
├─ esg_model_regression_fin.pkl
├─ esg_scaler_regression_fin.pkl
├─ esg_model_classifier_select.pkl
├─ esg_model_classifier_final_depth7.pkl
├─ xgb_model_ext.pkl
├─ scaler_ext.pkl
│
└─ data/
   ├─ X_features_fin.csv
   └─ fin/
      └─ fin_total_all_years.csv
