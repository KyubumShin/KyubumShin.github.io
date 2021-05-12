---
title: numpy 기초
date: 2021-05-04 23:05:32
category: numpy
thumbnail: { thumbnailSrc }
draft: false
---
나중에 찾아보기 귀찮아서 적는 numpy 기초 함수들
# numpy 함수
* 기본
```python
import numpy as np
```

1. Array 정의 함수   
기본적으로 numpy는 np.array()를 이용하여 아래와 같이 array를 정의 할 수 있다.
```python
data = [1,2,3,4,5]
arr = np.array(data)
```
arr은 다음과 같은 구조를 가진다


    array([1, 2, 3, 4, 5])

또한 shape 과 dtype 함수를 이용하여 arr가 몇 차원의 데이터인지, 자료형이 무엇인지도 알 수 있다.

```python
arr.shape
```




    (5,)




```python
arr.dtype
```




    dtype('int32')

2. Array 생성 함수
zeros, ones, arange   
np.zeros() : 영행렬을 생성  
np.ones() : 1로된 Array을 생성  
np.arange() : 값이 지정한 값만큼(default = 1) 증가하는 1차원 Array을 생성  
np.empty() : 임의로 지정된 초기값을 가지는 Array을 생성(0이 아닐수 있음)   
np.linspace() : 지정한 범위를 균등하게 나누는 Array을 생성   

```python
np.zeros((3,4))
```




    array([[0., 0., 0., 0.],
           [0., 0., 0., 0.],
           [0., 0., 0., 0.]])




```python
np.ones((6,3))
```




    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])




```python
np.arange(3,10,0.5)
```




    array([3. , 3.5, 4. , 4.5, 5. , 5.5, 6. , 6.5, 7. , 7.5, 8. , 8.5, 9. ,
           9.5])




```python
np.empty((3,5))
```




    array([[0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0.]])




```python
np.linspace(2,10, 3)
```




    array([ 2.,  6., 10.])




3. 기본연산
   * 산술연산   
    +, -, *, / 와 지수연산 ** 등 모든 산술연산은 Array의 elements 단위로 연산됨
   * 행렬의 곱   
    dot() 함수나, @(python > 3.5)을 이용하여 할수있다.  

```python
arr1 = np.array([[1,2,3],[4,5,6],[7,8,9]])
arr2 = np.array([[4,5,6],[4,5,6],[4,5,6]])
```


```python
arr1 + arr2
```




    array([[ 5,  7,  9],
           [ 8, 10, 12],
           [11, 13, 15]])




```python
arr1 - arr2
```




    array([[-3, -3, -3],
           [ 0,  0,  0],
           [ 3,  3,  3]])




```python
arr1 @ arr2
```




    array([[ 24,  30,  36],
           [ 60,  75,  90],
           [ 96, 120, 144]])




```python
np.dot(arr1,arr2)
```




    array([[ 24,  30,  36],
           [ 60,  75,  90],
           [ 96, 120, 144]])

