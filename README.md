# Dayschool Churn Prediction

**구독 기반 교육 플랫폼의 이탈 예측 및 해지 방지 캠페인 프로젝트**
(2024.08 \~ 2025.04)

---

## 프로젝트 개요

* **목표**:

  * 구독 서비스 해지(Churn) 가능성 높은 사용자 사전 예측
  * 예측 결과 기반 이메일 캠페인 실행 → 구독 유지율 개선 및 매출 손실 최소화
* **주요 내용**:

  * 학습·구독 로그 데이터 분석, 이탈 예측 모델 개발, 타겟 마케팅 캠페인 성과 평가 End-to-End 수행
* **데이터 출처**:

  * 내부 MySQL 데이터베이스에서 추출한 CSV (개인정보 제거 후 업로드)

---

## 디렉토리 구조

```text
Dayschool_Churn/
├── notebooks/
│   ├── 01_data_preprocessing.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_training_evaluation.ipynb
├── data/
│   ├── processed/
│   │   ├── dacon_user_id.csv
│   │   ├── project_progress_details.csv
│   │   ├── subscriptions.csv
│   │   ├── test_subscriptions.csv
│   │   ├── track_user_step_check_logs.csv
│   │   ├── track_users.csv
│   │   ├── train_subscriptions.csv
│   │   ├── user.csv
│   ├── results/
│   │   ├── debus/
│   │   │   ├── 2024-10-09_prediction_debug_LightGBM_0.8500.csv
│   │   │   ├── 2024-10-23_prediction_debug_LightGBM_0.8667.csv
│   │   │   ├── ...
│   │   ├── mail/
│   │   │   ├── 2024-10-09_mail_list.csv
│   │   │   ├── 2024-10-23_mail_list.csv
│   │   │   ├── ...
```
---

## 주요 파일 설명

| 파일명                                  | 설명                                  |
|-----------------------------------------|---------------------------------------|
| `01_data_preprocessing.ipynb`           | 원본 데이터 로딩/클렌징               |
| `02_feature_engineering.ipynb`          | 피처 엔지니어링/생성                  |
| `03_model_training_evaluation.ipynb`    | 모델 학습/검증/결과 분석              |
| `project_progress_details.csv`          | 프로젝트별 학습 로그                  |
| `subscriptions.csv`                     | 구독자 정보(이력/상태 포함)           |
| `train_subscriptions.csv`               | 학습용 구독 정보 (02_feature_engineering 결과)   |
| `test_subscriptions.csv`                | 테스트용 구독 정보 (02_feature_engineering 결과) |
| `track_user_step_check_logs.csv`        | 트랙 학습 로그                        |
| `track_users.csv`                       | 트랙 참여자 정보                      |
| `user.csv`                              | 사용자 메타 정보                      |
| `dacon_user_id.csv`                     | 내부 ID(익명화, 사내 식별용)           |



---

## 주요 결과 요약

* **이탈 예측 성능**:
  * **매주/격주별로 가장 성능이 우수한 모델(RandomForest, LightGBM, XGBoost 등)을 선정하여 예측에 활용**  
    (예: 2024-12-04 LightGBM F1-Score 0.88, 2025-04-09 RandomForest F1-Score 0.87 등)
  * 피처 중요도: `해지일_diff`, `구독_총수`, `user_id`, `구독 시작 월/일/시`, `last_activity_gap` 등
* **캠페인 효과**:
  * 타겟 캠페인(이메일) 도입 후 월 구독 해지율 평균 2.6%p 감소

