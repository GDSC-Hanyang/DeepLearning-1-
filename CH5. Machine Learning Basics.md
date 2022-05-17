Task(T)
====
features : 머신러닝을 진행하기 위한 어떤 물체나 사건으로부터 측정된 양
example : features 모음


classification : feature을 입력받아 어떤 카테고리에 속하는 지 예측하는 task
classification with missing inputs : 누락된 feature이 있는 경우
                                     여러 개의 함수를 정의해야 함
                                     변수 전체에 대한 확률 분포 학습
                                     누락된 입력 무시
                                     joint probability distribution 활용하여 하나의 함수로 표시
regression : continuous 수치 에측 task
transcription : 구조화되지 않은 표현에서 분리된 문자형식을 구분하는 task
machine translation : 기계 번역
structured output : 출력이 벡터 등 여러 값을 포함하는 자료구조 
anomaly detection : 비정상 입력 탐지
synthesis and sampling : 학습 데이터와 유사 데이터 생성
imputation of missing values : 입력 feature 중 누락값 예측
denoising : 노이즈 제거, 조건부 확률분포를 예측하는 것
density destimation or probability mass function estimation : 확률분포 함수를 찾음
                                                              다른 task를 위하여 사용
                                                              imputation of missing values task에서 누락된 값을 이 분포에서 찾음

performance measure(P)
===
머신러닝 알고리즘의 성능을 정량적으로 평가
accuracy : classification, transcription 등의 task에서의 지표
error rate : 얼마나 틀리는 가의 지표
log probability : 연속된 값의 성능지표

experience(E)
===
unsupervised learning algorithms : dataset의 구조로부터 유용한 속성을 찾음
supervised learning algorithms : 정답이 있는 dataset으로부터 학습
reinforcement learning : 고정된 dataset이 아니라 러닝시스템과 경험 사이의 피드백을 통해 학습
design matrix : 각 행에 다른 example이 있는 행렬

The no free lunch theorem
===

bayes error : 이론적 최소 오차
  -> 아무리 많은 데이터가 쌓여도 오차가 생길 수밖에 없음 (완전히 오차를 없앨 수는 없음)

만능 모델이 없으므로 특화된 모델을 만들 것

reguarization
---
적절한 함수의 종류를 선택해야함
regularizer : 모델의 underfit, overfit 경향을 조절 가능
              weight이 작을 수록 모델 단순화
              ![image](https://user-images.githubusercontent.com/89207256/168816831-5a633afe-d8f4-4e73-ac91-7a564443e051.png)

hyperparameters and validation sets
===
hyperparameter : feature의 차수, lambda 등 사용자가 설정해 주는 파라미터
validation set : 대게는 20% 정도의 dataset을 validation set으로 함

cross validation
---
dataset이 작을 경우 k-fold cross validation 사용
k개의 덩어리로 데이터를 겹치지 않게 나누고 돌아가면서 테스트셋으로 사용

예) test data 100개를 5개(k)의 set으로 나눔
    첫 4개를 train data로 사용
    나머지 1개를 test data로 사용
    -> 번갈아가면서 5번 실행 -> validation

Maximum Likelihood Estimation
===
좋은 estimator를 위한 특정 함수를 찾기 위함
-> empirical distribution을 따르는 expectation 식

KL divergence : empirical distribution과 유사하도록 학습한 distribution을 만듦
                cross-entropy와 동일
         
conditional log-likelihood and mean squared error
---
log(MLE)는 MSE와 동일하게 w를 예측
최적화하는 데에 MSE가 사용될 수 있음

properties of maximum likelihood
---
MLE
- consistency : 데이터가 늘어날 수록 정확함
- statistical efficiency : 한정된 데이터에서도 효과적
                           데이터 수가 적을 때 overfitting 위험이 있으므로 weight decay와 같은 regulatization 적용

Bayesian Statistics
===
frequentist statistics : 하나의 파라미터 값을 예측 -> 그에 대한 가능한 모든 예측을 알수 있음
bayesian statistics : 하나의 예측을 위해 가능한 모든 파라미터 값을 고려

vs MLE
  - MLE는 파라미터 값을 point estimate 하나를 사용하여 예측함
  - Bayesian statistics는 파라미터 값에 대한 모든 분포를 사용하여 예측함
  - 사전확률분포 사용 (prior distribution) -> 주로 gaussian distribution

MAP(maximum a postefiori) estimation
----
모든 bayesian posterior distribution을 구하면 비용이 많이 드므로
하나의 maximal posterior distribution을 구함


Supervised Learning Algorithms
===

probabilistic supervised learning
---
logistic regression : logistic sigmoid function을 사용하여 0,1 중 하나로 표현
(regression에서는 normal distribution 사용)

support  er vector machines(SVM)
----
kernel trick : 주로 gaussion kernel 사용, 연산 cost가 큼
SVM은 대부분 계수가 0이고 일부만 학습하여 완화함 (저 -> 고)
-> 학습 데이터 : support vector
2006년 Hinton에 의해 neural net이 RBF kernal SVM을 MNIST에서 이겨 딥러닝 시대 도래

other simple supervised learning algorithms
---
k-nearest neighbor (KNN) : 학습 단계도 없는 단순한 알고리즘
                           새로운 데이터 x에 대해 기존 데이터들과의 거리를 측정하여 이웃하는 데이터들의 평균 label을 구함
                           학습 모델이 없음
                           탐색 할 이웃 수 k는 적절히 정함
                           거리 측정법 : mahalanobis distance를 흔히 사용 (공분산 고려)
                           decision tree : 파라미터들을 각 영역에 따라 분리하는 알고리즘


Unsupervised Learning Algorithms
===
annotation, target, label이 없음
best representation 찾기 : 원본보다 단순하거나 이용하기 쉽게 만듦
  - low-distansional represetations : 차원을 압축
  - sparse representations : 정보의 대부분을 0으로 만듦 (차원 늘림)
  - independent representations : 데이터 소스를 독립적인 차원으로 분리함


Stochastic Gradient Descent(SGD)
===
대부분의 딥러닝 알고리즘에 적용
기존의 gradient descent는 연산시간이 오래 걸리므로 cost의 평균으로 한번에 계산
전체 데이터 사이즈에 상관없이 작은 개수의 부분 데이터만큼씩 학습

data set - cost function - optimization 순으로 만듦

challenges motivation deep learning
===

1.The curse of dimensionality (차원의 저주)
---
차원이 늘 때마다 데이터의 양은 지수 배만큼 엄청나게 늘어난다

2.local constancy and smoothness regulatization
---
prior belief : 어떤 종류의 함수를 학습해야 하는가에 대한 prior belief 
               sample이 약간 달라져도 prior가 있어 학습 결과는 크게 달라지지 않음
               
3.manifold learning
---
manifold : 이어진 지역, 각 점 주위 이웃과 이어진 점들의 집합
manifold learning : manifold를 따라서만 움직이도록 제한된 상태에서의 러닝
                    probability mass가 매우 집중되어 있다고 가정한 것임
manifold hypothesis : image, test, sound 데이터는 특정 manifold에 분포되어 있음
                      잡음만 있는 화면이나 그냥 나열된 알파벳을 러닝했을 때 어떤 의미를 절대 찾을 수 없음

