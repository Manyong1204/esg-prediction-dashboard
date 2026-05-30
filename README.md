# ESG Prediction Dashboard

재무 및 비재무 데이터를 기반으로 기업의 차년도 ESG 등급을 예측하는 Streamlit 기반 머신러닝 대시보드입니다.

본 프로젝트는 ESG 등급 예측 문제를 회귀와 분류 관점에서 비교 분석하고, 최종적으로 XGBoost 기반 다중분류 모델을 활용하여 기업별 ESG 등급 예측 및 개선 전략을 제안하는 것을 목표로 합니다.

<br>

## Demo

- Streamlit App: https://esg-prediction-dashboard.streamlit.app/
- GitHub Repository: https://github.com/Manyong1204/esg-prediction-dashboard

<br>

## Project Overview

ESG 평가는 기업의 지속가능성과 투자 매력도를 판단하는 중요한 지표입니다.

본 프로젝트에서는 기업의 재무 지표와 일부 비재무 지표를 활용하여 차년도 ESG 등급을 예측하고, 예측 결과를 시각적으로 확인할 수 있는 대시보드를 구현했습니다.

주요 목표는 다음과 같습니다.

- 재무 및 비재무 지표 기반 ESG 등급 예측
- 회귀 모델과 분류 모델의 성능 비교
- XGBoost 기반 최종 예측 모델 구축
- SHAP 분석을 통한 예측 근거 해석
- 기업 검색 및 지표 시뮬레이션 기능 제공
- ESG 등급 개선을 위한 주요 변수 제안

<br>

## Tech Stack

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

## Main Features

### 1. ESG Rating Prediction Dashboard

기업명 또는 종목코드를 검색하여 특정 연도의 ESG 등급을 확인하고, AI 모델의 예측 등급과 실제 등급을 비교할 수 있습니다.

### 2. Regression Analysis

초기 회귀 모델의 설명력을 확인하고, 파생변수 추가 및 Rolling Window 분석을 통해 모델 성능 개선 과정을 시각화했습니다.

### 3. Classification Analysis

ESG 등급 예측 문제를 다중분류 문제로 재정의하고, Logistic Regression, Random Forest, SVM, LightGBM, XGBoost 모델의 성능을 비교했습니다.

### 4. Final Model Selection

최종 모델로 XGBoost 기반 분류 모델을 선정했습니다.

과적합 가능성을 고려하여 max_depth 튜닝 결과를 비교하고, 일반화 성능을 기준으로 최종 모델을 선택했습니다.

### 5. SHAP-based Model Interpretation

SHAP 분석을 통해 각 변수가 ESG 등급 예측에 미치는 영향을 시각화했습니다.

이를 통해 단순 예측 결과뿐 아니라, 모델이 어떤 근거로 등급을 판단했는지 확인할 수 있도록 구성했습니다.

### 6. Feature Simulation

사용자가 주요 지표 값을 직접 조정하면 ESG 예측 등급이 어떻게 변화하는지 확인할 수 있습니다.

또한 목표 등급 상승을 위해 어떤 변수를 개선하면 좋을지 제안합니다.

<br>

## Model Performance

| Stage | Metric | Score |
|---|---:|---:|
| Previous Research | R² Score | 0.225 |
| Initial Regression | R² Score | 0.440 |
| Advanced Regression | R² Score | 0.585 |
| Final Classification | ROC-AUC | 0.829 |

<br>

## Project Structure

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
```

<br>

## How to Run

### 1. Clone Repository

```bash
git clone https://github.com/Manyong1204/esg-prediction-dashboard.git
cd esg-prediction-dashboard
```

### 2. Create Virtual Environment

```bash
conda create -n project02 python=3.10
conda activate project02
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Streamlit App

```bash
streamlit run app.py
```

<br>

## Requirements

본 프로젝트는 SHAP과 XGBoost의 버전 호환성을 고려하여 아래 버전을 사용했습니다.

```txt
xgboost==3.0.3
shap==0.49.1
```

전체 주요 패키지는 다음과 같습니다.

```txt
streamlit
pandas
numpy
plotly
matplotlib
scikit-learn
joblib
lightgbm
xgboost==3.0.3
shap==0.49.1
```

<br>

## Team

| Name | Role |
|---|---|
| Park Hyun-woo | Modeling, Data Processing |
| Min Sun-ah | Data Analysis, Dashboard Development, Model Interpretation |

<br>

## My Contribution

- Streamlit 기반 ESG 예측 대시보드 구현
- 기업 검색 및 예측 결과 출력 기능 구성
- 회귀 모델과 분류 모델의 성능 비교 결과 시각화
- XGBoost 최종 모델 결과 및 Feature Importance 시각화
- SHAP 기반 예측 근거 분석 화면 구현
- 지표 시뮬레이션 및 개선 전략 제안 기능 구성
- GitHub 및 Streamlit Cloud 배포 환경 구성

<br>

## Future Improvements

- 최신 ESG 평가 데이터 추가 확보
- 산업군별 모델 분리 및 성능 비교
- 정성적 ESG 공시 데이터 반영
- 예측 결과 설명력 고도화
- 사용자 입력 기반 리포트 자동 생성 기능 추가

<br>

## Notes

본 프로젝트는 포트폴리오 및 학습 목적으로 제작되었습니다.

데이터와 모델 파일은 프로젝트 실행을 위해 필요한 범위 내에서 구성되었으며, 공개 가능한 데이터만 포함하는 것을 원칙으로 합니다.

<br>

## License

This project is for portfolio and educational purposes.
