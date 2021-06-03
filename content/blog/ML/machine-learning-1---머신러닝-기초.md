---
title: Machine Learning 1 - 머신러닝 기초
date: 2021-05-27 09:05:25
category: ML
thumbnail: { thumbnailSrc }
draft: false
---
# 머신러닝 기초
## 0. Machine Learning(기계학습) 이란?
* 경험을 통해 자동으로 개선하는 컴퓨터 알고리즘
* 학습데이터를 통해 목표값(target)을 예측하는 함수 $y(x)$ 를 최적화 시키는 학습

## 1. 머신러닝의 핵심 개념
* 학습단계(training phase) : 함수를 학습데이터에 기반하여 최적화 하는 단계
* 테스트셋(test set) : 모델을 평가하기 위해서 사용하는 데이터
* 일반화 : 학습단계에서 사용되지않은 새로운 데이터에 대하여 바르게 측정할 수 있는 역량(test set으로 수행하는 평가항목)
* 지도학습(supervised learning) : target이 주어진경우
  * 분류(classification)
  * 회귀(regression)
* 비지도학습(unsupervised learning) : target이 주어지지 않는경우
  * 군집(clustering)
* 강화학습(Reinforcement learning) : 행동에 의한 가중치를 통한 최적 행동 학습

## 2. 기초
* 다항식 곡선 근사(Polynomail Curve Fitting)(다항식 회귀분석)
  * 주어진 입력벡터로 다항식을 예측하는것

<p align="center"><img src="./PCF.png"></p>
<center>Ex) 아래의 점들로 sin곡선을 예측하여야한다!  </center>
<br></br>

아래와 같은 식을 사용한다. 입력받는 x에 대하여 최적화된 파라미터 $\mathbf{w}$를 찾는것이 목표이다.

$$
y(x,\mathbf{w}) = w_{0} + w_1x+w_2x^2 + ... + w_Mx^M = \sum_{j=0}^{M}w_jx^j
$$

* 오차함수(Error Function)
  예측한 입력받은 데이터와 예측함수간의 오차를 나타내는 함수(추후에 자세히 다룰 예정)
$$
E(\mathbf{w}) = \frac{1}{2}\sum_{n=1}^{N}\left\{ y(x_n, \mathbf{w})-t_n\right\}^2
$$ 

* 과소적합과 과대적합
  * 과소적합(Under-fitting)  
    학습데이터로 충분히 학습되지 못한 상태. 파라미터가 너무 단순해서 제대로 나타내지 못하는 경우나, 데이터가 부족할경우 발생
  * 과대적합(Over-fitting)
    학습은 완료되었으나 학습데이터의 편향(bias)까지 학습해버린 경우. 이럴경우에는 테스트에서 일반성을 가지지 못하는경우가 많다.

* 규제화  
  * 파라미터가 너무 커지는것을 방지하기 위한 방법
  * $\lambda$ 라는 변수를 두어 파라미터의 절대값을 조절한다
$$
E(\mathbf{w}) = \frac{1}{2}\sum_{n=1}^{N}\left\{ y(x_n, \mathbf{w})-t_n\right\}^2 + \frac{\lambda}{2}\left \| \mathbf{w} \right \|^2
$$ 

