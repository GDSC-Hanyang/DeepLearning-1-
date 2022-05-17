Why probability?
=====
딥러닝 적용 대상은 uncertainty가 많기 때문에 확률을 이용

#Uncertainty Source


1. Inherent stochasticity 
모델링된 시스템의 고유한 확률적인 부분 (양자역학)


2. Incomplete observability
불완전한 관찰능력 (Monty Hall problem)

3. Incomplete modeling
불완전한 모델링 (정보의 부족)
복잡하지만 확실한 규칙보다 단순하지만 불확실한 규칙이 더 실용적

degree of belief : 0 또는 1 (0% 또는 100%)
frequentist probability : 조건부 확률 -> 객관적이고 직접적으로 표현가능한 확률
Bayesian probability : 정량적 수준과 연관된 확률 -> 사전확률과 가능성을 토대로 사후확률을 추정
                      ![image](https://user-images.githubusercontent.com/89207256/168791839-9e0eaeed-a2be-4b71-bf91-00859c81e75c.png)



Loss Function
====
손실함수 : 모델이 얼마나 잘 예측하는지를 평가하는 지표


cross entropy error (CEE)
---
classification(이산적 분포를 갖는 데이터)에서 이용하는 손실함수

entropy : 불확실성에 대한 척도, 불확실성이 커질수록 entropy도 커짐 (예측하기 쉬울 수록 entropy가 낮다)
![image](https://user-images.githubusercontent.com/89207256/168785313-9c6388e5-8feb-47be-9d66-8c9d33ca4032.png)

![image](https://user-images.githubusercontent.com/89207256/168785782-ba37c36c-bca7-446c-97bf-aa0d5b1ea12f.png)
역전파 시 기울기 손실이 덜하며 속도도 더 빠르므로 역전파에 유리함
중간층에서는 활성 함수에 대한 미분 값 사용 -> gradient vanishing이 일어남

classification을 수행하는 모델에서 CEE는 정답인 클래스에 대해 오차를 계산함



mean squared error (MSE)
---
regression(연속적 분포를 갖는 데이터)에서 이용하는 손실함수

![image](https://user-images.githubusercontent.com/89207256/168786468-c20c7f2d-c3fe-4024-93c3-9fbe0c536e95.png)

정답과 예측값 사이의 차이를 통해 오차를 계산함


Maximum-Likelihood
====
모델의 학습 : 정확한 y값을 찾는 것보다 y를 평균으로 하는 분포에 의한 파라미터 (평균,표준편차)를 찾는 것
1. 모든 데이터가 각각 독립적이다.
2. 각각의 데이터가 동일한 분포를 가진다.
  -> x는 관측 데이터로 고정, y를 가장 잘 설명하는 파라미터를 찾고자 하는 것
  
 모델 최적화 시 Maximum을 구하는 것보다 Minimize를 많이 사용하므로 negative-likelihood를 사용
 ![image](https://user-images.githubusercontent.com/89207256/168787703-bdac9849-c392-4775-8745-3379ed440ed3.png)


Activation Function
====
![image](https://user-images.githubusercontent.com/89207256/168788585-bcd26da0-2899-4bfb-85ae-fde312d7c45f.png)

네트워크에서 전달된 값이 임계치 이상인지 여부를 판단하여 임계치보다 높으면 y=1, 임계치보다 낮으면 y=0을 전달하는 함수
![image](https://user-images.githubusercontent.com/89207256/168788796-70c87307-a114-4fee-9933-e6d069801a5c.png)


1.sigmoid (시그모이드)
----
0~1 사이값으로 logistic regression 함수이고 간단한 분류문제, 딥러닝 초기에 많이 사용


한계 1) vanishing gradient problem : 중심 0에서 멀어질수록 미분값이 작아져 역전파 시 값이 소실됨
한계 2) outputs not zero centered : sigmoid로 인해 모든 입력값(x)가 +가 되어 모든 wi가 + 나 -의 같은 방향을 가져야하나 만약 해가 다른 방향에 있을 경우 비효율적인 탐색 발생
한계 3) exponential function computationally expensive : 비용이 높음


![image](https://user-images.githubusercontent.com/89207256/168789799-cb97179d-fad6-4dfd-87c2-e151ff94cfc1.png)



2.tanh (hyperbolic tangent function)
----------
-1~1 사이 값으로 그래프 중심이 0으로 이동
sigmoid의 한계2 문제 해결


한계) 중심값에서 멀어지면 역전파 시 vanishing gradient problem 문제가 남아있음
![image](https://user-images.githubusercontent.com/89207256/168790450-2e07b1eb-9d00-4c16-a1eb-1361a0d3172c.png)


3.ReLU (rectified linear unit)
---
간단하여 학습속도가 빠르고, 역전파 시 vanishing gradient 문제를 해결


한계) 0 이하 값에 대해서는 모두 0이므로 이 경우 학습이 안됨
![image](https://user-images.githubusercontent.com/89207256/168790557-7ca2b681-5ff9-452e-87a2-5540c9737dc3.png)


4.Leaky ReLU (rectified linear unit)
---
ReLU를 보완하여 0 이하 값에 대해서 학습이 가능하도록 함
![image](https://user-images.githubusercontent.com/89207256/168790688-8aac9686-4bed-41a3-810d-b01abdeab604.png)


5.ELU (Exponential linear unit)
---
0보다 작은 경우 지수함수를 이용하여 미분이 가능하도록 함
![image](https://user-images.githubusercontent.com/89207256/168790844-8518fefa-44cb-4845-b6c3-46820ac9803f.png)



6.Swish
---
image-net에서 다른 함수들보다 좋은 성능을 냄
![image](https://user-images.githubusercontent.com/89207256/168790988-cc9a4beb-ba5f-4066-8cdf-8fd5b43cc60d.png)


7.softplus
---
sigmoid의 적분함수
exponential function computationally expensive
![image](https://user-images.githubusercontent.com/89207256/168791088-cdba86ad-f5bd-44bb-a66b-9e0c89f468b5.png)

![image](https://user-images.githubusercontent.com/89207256/168792048-014f9a98-fc1a-4b6b-91d3-7b80e63c6667.png)


출처 : https://blog.naver.com/kiakass/222189684407
