#eigendecomposition


eigenvector(고유벡터) 
----
선형변환을 거쳤을 때 방향은 바뀌지 않고 크기만 변하는 벡터
matrix의 column 개수만큼 (차원의 개수만큼) 존재

![image](https://user-images.githubusercontent.com/89207256/161242862-cfa078e4-98c9-45d8-9a1c-0f5b745e5155.png)

eigenvalue(고유값)
----
고유벡터들의 변화한 크기값
matrix의 차원의 개수와 동일

$$
A v =\lambda v
$$


$$
A = V diag(\lambda) V^{-1}
$$

V : eigenvector 
eigenvector들은 서로 수직이므로
$$ V^{-1} = V^{T} $$


\[
A = UDV^{T}
\]



#Moore-Penrose pseudoinverse


유사역행렬

정의 : ![image](https://user-images.githubusercontent.com/89207256/161244891-e8cf7c77-e4bc-4533-a0fd-b9435b46e4ea.png)


공식 : $$ A^+ = VD^+ U^T
