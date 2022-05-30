Deep Feedforward Networks
====
= feedforward neural network 

= multilayer perceptrons (MLP)

deep learning
---
f(x) = f_3(f_2(f_1(x)))와 같이 여러 겹의 depth로 사용하기도 함
중간 layer는 결과를 직접 사용하지 않으므로 hidden layer라고도 함
width : 각 layer 벡터의 차원


linear model은 2개 이상의 입력 변수 간 상호작용을 이해x

nonlinear transformation 사용
-> 학습하여 일반적인 transformation을 사용하거나 메뉴얼하여 사용


-Learning XOR

![image](https://user-images.githubusercontent.com/89207256/169994670-0dc821be-1272-43da-b05d-b7cf10069262.png)
Matrix를 사용하여 왼쪽->오른쪽 으로 단순하게 표현 가능

두 개의 layer를 사용해도 둘 다 linear function이면 한 개의 layer을 사용한 모델과 동일해짐

ReLU(Rectified Linear Unit)와 같은 activation function을 사용하여 h가 nonlinear function이 되도록 함
![image](https://user-images.githubusercontent.com/89207256/169995150-089dd1bf-dc50-482d-8a40-3485c9a2d060.png)
이를 만족하는 W,c,w는 무한함
-> gradient descent를 사용하여 error 최소화


Gradient Based Learning
====

loss function이 convex하지 않다는 점에서 머신러닝 모델과 다름
gradient : 초기에 랜덤 -> 학습 -> 수렴


Cost Functions
---
MLE(cross-entropy)를 cost function으로 사용한다는 점에서 머신러닝 모델과 동일

- Mean Squared Error 

무한히 많은 샘플들을 학습시킬 수 있다면, MSE 최소화 = 각 x값에 대한 y의 평균 예측
![image](https://user-images.githubusercontent.com/89207256/169997066-a161429b-54d2-4eca-9e8f-0bfb7a0d953c.png)

![image](https://user-images.githubusercontent.com/89207256/169997105-b316656e-5c47-419e-904d-bc74f0bcf9d0.png)


- Mean Absolute Error

최적화한 함수들 집합으로 묘사 -> 각 x에 대한 t의 중간값 예측
![image](https://user-images.githubusercontent.com/89207256/169997837-4d07ed42-19b1-4ed6-8e2c-8bce24f924bc.png)

