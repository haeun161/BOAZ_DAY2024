# BOAZ_DAY2024
주제: 차량 침입 탐지를 위한 AI 모델 개발

## 대회 정보
- [Kaggle Competition](https://www.kaggle.com/competitions/boaz-day-2024)

## 최종 순위
- Public, Private Score 모두 1위, 대상 수상

## EDA
- 자세한 것은 발표자료에서 확인 가능
#### 도메인 분석과 전처리
   - Timestamp, CAN_ID에 따라 Class 분포를 비교한 결과, 특정 공격에 있어서 특징을 파악했다
     - Flooding은 특정 시간대에 동시다발적으로 CAN 메시지를 대량 전송하는 특징을 보인다
     – Malfunction은 기존 차량의 CAN_ID를 선별적으로 타겟팅하여 계속 공격하는 특징을 확인
   - 공격 유형별 Data 열의 바이트 분포를 분석하여 바이트 별 특성을 고려하여 새로운 열 추가
   - Time Stamp에 따른 공격 이벤트를 확인 결과, 동일한 시간대에 집중적으로 분포 확인 => 시간순으로 정렬 후, Lag 반영한 파생 변수 생성
   - 유클리드 거리와 유클리드 거리차 반영
   - 데이터 불균형을 맞추기위한 SMOTE 방식의 statistic한 데이터 증강 방법 사용
   - Random Forest 모델에서 제공하는 Feature Importance 반영

## 모델링
- timestemp의 특징만 보고 자칫하면 RNN 모델이 성능이 좋을 것 같지만, 이외에 공격의 비선형적인 관계들을 포함하기에 트리 모델가 가장 적합하며, 성능이 높았음
- ExtraTrees, Random Forest, XGBoost 순으로 성능이 가장 좋았음

### 📂 프로젝트 발표 자료  
- 📑 [PPT 보기 (Google Drive)](https://drive.google.com/file/d/1I-yRP-GrMNU66RD5ZU8WUvM5ks687pke/preview)

