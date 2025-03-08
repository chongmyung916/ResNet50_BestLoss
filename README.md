# ResNet50_BestLoss
ResNet50 모델을 이용해서 benign vs melanoma 예측하기(best min loss 기준)

# Result
- melanoma vs benign classification problem을 resNet모델을 이용해서 예측, 평가했는데 batch size가 16일때 모든 지표(acc, auc, precision, recall)가 가장 잘나왔다.
- 배치 64, 128이 2,3번째로 성능이 좋았다. 그런데 배치 64일때는 accuracy는 128보다 높은데 auc는 또 128일때가 64일때보다 더 컸다. 배치사이즈 32일때는 4가지 케이스 중 가장 낮게 나왔다.

# Analysis
- batch size 분석
  - 작은 배치: 더 나은 일반화 성능(학습 과정에 잡음을 추가하여 모델이 다양한 데이터 패턴을 학습), 모델 학이 불안정할 가능성 있음(경사 하강의 변동성을 증가, 수렴하지 못할 위험이 생김).
  - 큰 배치: 학습 안정화(경사 하강의 변동성을 줄인다, noise 낮춰 빨리 수렴), 일반화 성능 저하될 수 있음(지역 최적점(local minima)에 갇힐 위험). 학습 데이터에 과적합되어 예측 성능이 떨어질 수 있음.
