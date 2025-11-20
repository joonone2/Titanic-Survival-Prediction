# Titanic Survival Prediction

A machine learning project to predict passenger survival on the Titanic using structured data, feature engineering, and ensemble modeling.

## 📁 Project Structure

```
📂 project_root
 ├── data/              # Raw & processed datasets
 ├── notebooks/         # Jupyter notebooks for EDA, modeling
 ├── src/               # Python source code
 ├── models/            # Saved models
 ├── submissions/       # Kaggle submission files
 └── README.txt
```

## 🎯 Project Goal

Kaggle Titanic 데이터를 이용해 승객 정보를 바탕으로 생존 여부를 예측하는 모델을 만드는 프로젝트입니다.

## 🧹 1. Data Preprocessing

* Age 결측치: Title 기반 그룹 평균으로 대체
* Embarked 결측치: 최빈값으로 대체
* Fare 이상치 완화: log 변환 적용
* 범주형 인코딩: Sex, Pclass, Embarked, Title → One-Hot Encoding
* 파생 변수 생성:

  * FamilySize = SibSp + Parch + 1
  * IsAlone = 1 if FamilySize == 1 else 0

## 📊 2. Exploratory Data Analysis (EDA)

EDA에서 확인한 주요 인사이트:

* 여성 생존률 > 남성 생존률
* 1등급 > 2등급 > 3등급 순으로 생존률 높음
* 어린 승객(아동)은 생존률이 높음
* Title은 생존 예측에 유용한 특징

## 🛠 3. Modeling

사용한 모델:

* Logistic Regression
* Random Forest
* XGBoost

### Hyperparameter Tuning

* GridSearchCV를 활용해 각 모델 최적화

### Ensemble Model

* Soft Voting
* 구성: Logistic Regression + XGBoost
* 최종 Weight: (1, 2)

## ✅ 4. Final Model Performance

Validation Accuracy: **0.8603**
AUC: **0.87**

Kaggle Private Score: **0.775**

## 📤 5. Submission

최종 제출 파일 구조:

```
PassengerId,Survived
892,0
893,1
...
