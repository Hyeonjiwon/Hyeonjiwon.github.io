---
title: '[머신러닝] Eigen Decomposition' 
excerpt: '고유값 분해, 고유값과 고유 벡터'
categories:
    - Machine Learning

tag:
    - ML
    - EigenValue
    - EigenVector
    - EigenDecomposition

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2020-04-29T18:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true

published : false
---

## 고유벡터(Eigen Vector)
선형 변환의 고유 벡터는 그 선형 변환이 일어난 후에도 방향이 변하지 않는, 영벡터가 아닌 벡터입니다. 

## 고유값 (Eigen Value)
고유 벡터의 길이가 변하는 배수를 선형 변환의 그 교유 벡터에 대응하는 고유값(eigenvalue)라고 합니다. 
Av = λv (A : linear transformation, v : eigenvector, λ : eigenvalue, scala)
 


https://ko.wikipedia.org/wiki/%EA%B3%A0%EC%9C%B3%EA%B0%92%EA%B3%BC_%EA%B3%A0%EC%9C%A0_%EB%B2%A1%ED%84%B0
det(xI - T) = 0, 즉 x가 고유 다항식의 근임

## 고유값 분해 (Eigen Decomposition)
고유값 분해(eigen decomposition)는 고유값과 고유벡터로부터 유도되는 고유값 행렬과 고유벡터 행렬에 의해 분해될수있는 행렬의 표현입니다.
선형대수학에서, 고유값 분해는 매트릭스(행렬)를 정형화된 형태로 분해함으로써 행렬이 고유값 및 고유 벡터로 표현됩니다. 대각화 가능 행렬만이 인수분해될 수 있습니다.
대각화 가능 행렬(diagonalizable matrix)은 적절한 가역 행렬로의 켤레를 취하여 대각 행렬로 만들 수 있는 정사각 행렬입니다. 
가역 행렬(invertible matrix) 또는 정칙 행렬(regular matrix) 또는 비특이 행렬(non-singular matrix)은 그와 곱한 결과가 단위 행렬(identity matrix, 주대각선의 원소가 모두 1이며 나머지 원소는 0인 정사각 행렬)인 행렬을 갖는 행렬입니다. 이를 그 행렬의 역행렬(inverse matrix)이라고 합니다.

수정중...