overflow and underflow
===
rounding error (반올림 오차) : 오류 누적을 최소화하도록 설계되지 않으면 문제가 될 수 있음
underflow : 0 근처의 값이 0으로 반올림되어 오류가 발생하는 경우 대비가 필요함
overflow : 수가 너무 커 비트 초과된 경우
softmax function : multinoulli distribution (k개 중 선택 문제)에서 확률 예측할 때 사용
                   softmax(z), log softmax(x) 등의 방법으로 overflow/underflow 해결 가능함
                   실제로 적용할 때 low level library 잘 사용하면 걱정 없이 해결됨
                   ![image](https://user-images.githubusercontent.com/89207256/168806461-009f2333-fca7-4012-bda6-d9aa515f7dcd.png)

poor conditioning 
===
conditioning : 작은 입력의 변화에 얼마나 빨리 함수가 변하는가
condition number : 행렬이 eigenvalue decomposition이 가능할 때 가장 큰 고유치와 가장 작은 고유치의 비 값이 크면 입력의 오차에 민감하다
                  ![image](https://user-images.githubusercontent.com/89207256/168807025-2348ac8b-cef1-41a7-8404-8dd542cc82e1.png)
                    
                    
                    민감도는 행렬의 고유 문제
                    poor conditioned 행렬은 역행렬로 곱해질 때 오차를 증폭함


gradient-based optimization
===
objective function (criterion) : 최적화 과정에서 우리가 최소/최대화시키고 싶은 함수
cost function (loss function, error function) : 목적함수 중 최소화시키는 경우
gradient descent : 미분의 반대 부호의 방향으로 작은 스텝 움직이면서 함수값을 줄이는 방법\
critical points (stationary points) : 미분이 0이 되는 점
local minimum : 모든 이웃하는 f(x)값보다 작은 f(x)를 갖는 점 (피해야 함)
saddle points : f(x)의 미분은 0이나 local minimum이나 local maximum이 아닌 경우
global minimum : f(x) 중 가장 작은 값
directional derivative : f(x)의 경사
method of steep descent (gradient descent) : f(x)를 최소화하려는 빠르게 f(x)를 감소시키게 하는 방법을 찾아야 함
                                             이 최소화의 방향은 바로 gradient의 반대방향임
                                             ![image](https://user-images.githubusercontent.com/89207256/168807998-4759f7cc-1aa8-479d-bf7d-7b770e254f49.png)
line search : 몇 개의 learning rate를 f(x)에 대입해 봐서 가장 좋은 것을 찾는 방법
gradient descent의 단점은 미분이 0 근처에서 수렴할 때 학습이 느려지므로 이 때는 직접 미분을 하기도 함


beyond the gradient : jacobian and hessian matrices
===
jacobian matrix : 입력과 출력이 모두 벡터인 함수의 편미분
second derivative (curvature : 곡률) : 미분의 미분
hessian matrix : 여러 차원의 입력의 경우 여러 이차미분이 있을 수 있으며, 이를 모은 행렬
                 hessian = gradient의 jacobian
                 편미분의 순서는 바뀌어도 됨
                 hessian과 이차미분을 사용하여 learning rate를 정할 수 있음
second derivative test : critical point가 local minimum/maximum, saddle 중 무엇인지 알려줌 by hessian
newton's method : second order taylor series expansion을 사용하여 x가 0 근처의 f(x)를 근사화
first order optimization altorithms : gradient descent
second order optimization altorithms : newton's method
lipschitz continuity : 약한 제약을 걸어 최적화 보장
convex optimization : 강한 제약을 걸어 최적화 보장 -> convex function에서만 적용가능


constrained optimization
===
: 일정 set 안의 x에 대해 최적화


간단한 방법 : 경사하강 스텝에서 결과가 set으로 돌아오도록 사영함
복잡한 방법 : unconstrained 최적화 문제를 constrained 최적화 문제로 바꿈
Karush-Kuhn-Tucker (KKT) approach : generalized lagrangian
                                    ![image](https://user-images.githubusercontent.com/89207256/168809970-66184544-7795-4b21-9239-893b5b18d32c.png)


linear least squares
===
![image](https://user-images.githubusercontent.com/89207256/168810119-c7b90381-63c7-4372-a158-af7b1d7a2d46.png)


gradient descent : ![image](https://user-images.githubusercontent.com/89207256/168810251-09e518b8-70bd-4fe9-b1b8-b38dc6a119aa.png)
newton's method : true function이 quadratic이므로 한번에 global minimum을 구할 수 있음
lagrangian : 제약조건 추가
             제약 조건을 넘어가는 경우에는 gradient ascent로 제약 조건을 만족하도록 함

출처 : https://blog.naver.com/sparko7/221546751620
