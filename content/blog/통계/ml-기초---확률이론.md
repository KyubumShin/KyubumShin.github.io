---
title: ML 기초 - 확률이론
date: 2021-05-28 06:05:80
category: 통계
thumbnail: { thumbnailSrc }
draft: false
---

# 확률 이론
## 기본 용어
### 확률 변수
* 확률변수 $X$는 표본의 집합 $S$의 원소 $e$를 실수값 $X(e) = x$ 에 대응시키는 함수
* ex) 동전던지기의 경우에서 생각해보자
  * $S = \left \{앞면, 뒷면\right \}$
  * $X(앞면) = 0, X(뒷면) = 1$ 로 대응시킬수 있다
* 대문자 $X, Y, ...$ : 확률 변수
* 소문자 $x, y, ...$ : 확률변수가 가질 수 있는 값
* 확률 $P$는 집합 $S$의 부분집합을 실수값에 대응시키는 함수

### 누적분포함수(cumulative distribution function, CDF)
* 주어진 확률변수가 특정 값보다 작거나 같은 확률을 나타내는 함수
$$
F(x) = P\left [X\in (-\infty,x)  \right ]
$$
### 연속 확률변수
* 누적 분포함수 $F(x)$를 가진 확률변수 $X$에 대하여 $f(x)$가 존재한다면(구간내에서  연속이라면) $X$를 연속확률 변수라고 부르고, $f(x)$를 $X$의 확률밀도함수(Probability density function, PDF)라고 부른다
$$
F(x) = \int_{-\infty}^{x}f(t)dt
$$

### 확률변수의 성질
* 덧셈법칙
$$
p(X) = \sum_Yp(X,Y)
$$
* 곱셈법칙
$$
p(X,Y) = p(X|Y)p(Y) = p(Y|X)p(X)
$$
* 베이즈 확률(Baeys)
$$
p(Y|X) = \frac{p(X|Y)p(Y)}{\sum_Yp(X|Y)p(Y)}
$$

### 확률변수의 함수
* 확률변수는 함수이기때문에 확률변수의 함수 $Y = f(X)$ 도 확률변수
* $Y = g(X) 가 존재하고 그 역함수가 존재할 때 다음이 성립
  * 단일변수
$$
p_y(y) = p_x(x)\left | \frac{dx}{dy} \right |
$$  
  * 여러변수(벡터) ($\mathbf{y} = \mathbf{g(x)}$ 가 1대1 변환일경우)
$$
p_y(y_1,...,y_k) = p_x(x_1,...,x_k)\left | \mathbf{J} \right | \\
$$
$$
\mathbf{J} = \begin{bmatrix}
\frac{\partial x_1}{\partial y_1} & \frac{\partial x_1}{\partial y_2} & \cdots  & \frac{\partial x_1}{\partial y_k}\\ 
\frac{\partial x_2}{\partial y_1} & \cdots &  & \vdots \\ 
\vdots  &  &  & \\ 
\frac{\partial x_k}{\partial y_1} & \cdots &  & \frac{\partial x_k}{\partial y_k}
\end{bmatrix}
$$

* Inverse CDF Technique
* 확률변수 $X$에 대한 CDF $F_x(x)$가 존재하고, 연속확률분포함수 $U\sim UNIF(0,1)$의 함수로 정의되는 다음의 확률변수 $Y$가 다음과같을때
$$
Y = F_x^{-1}(U)
$$
  확률변수 Y 는 확률변수와 동일한 분포를 따르게 된다.
$$
\begin{aligned}
F_Y(y) &= P \left [ Y \leq y \right ]\\
&= P \left [ F_x^{-1}(U) \leq y \right ]\\
&= P \left [ U \leq F_x(y) \right ]\\
&= F_x(y)
\end{aligned}


$$
### 기대값(Expectations)
* 각 사건이 벌어졌을때의 수치와 그 확률을 곱한것을 전체사건에 대해 합한값(확률분포 $p(x)$에서 함수 $f(x)$의 평균값)
* 이산확률분포(discrete distribution) : $\mathbb{E} \left [ f \right ] = \sum_x p(x)f(x)$
* 연속확률분포(continous distribution) : $\mathbb{E} \left [ f \right ] = \int p(x)f(x)dx$
* 확률분포로부터 N개의 샘플을 추출해서 기대값 근사가능
$$
\mathbb{E} \left [ f \right ] = \frac{1}{N}\sum_{n=1}^{N}f(x_n)
$$
* 다변수함수
$$
\mathbb{E}_x \left [ f(x,y) \right ] = \sum_x p(x)f(x,y)
$$
$$
\mathbb{E}_{x,y} \left [ f(x,y) \right ] = \sum_x p(x|y)f(x,y)
$$
* 조건부 기대값
$$
\mathbb{E}_x \left [ f|y \right ] = \sum_x p(x|y)f(x)
$$

## 분산(variance), 공분산(covariance)
* 분산 : $var[f] = \mathbb{E}_x [ (f(x) - \mathbb{E}[f(x)] )^2] = \mathbb{E}[f(x)^2] - \mathbb{E}[f(x)]^2$
* 두개의 확률변수 $x, y$ 에대한 공분산
$$
\begin{aligned}
cov[x,y] &= \mathbb{E}_{x,y}[\left \{ {x} - \mathbb{E}[{x}] \right \}\left \{ {y^T} - \mathbb{E}[{y^T}] \right \}] \\
&= \mathbb{E}[xy] - \mathbb{E}[x]\mathbb{E}[y]
\end{aligned}

$$

* $\mathbf{x,y}$가 각각 확률변수의 벡터라고 할때
$$
\begin{aligned}
cov[\mathbf{x,y}] &= \mathbb{E}_{x,y}[\left \{ \mathbf{x} - \mathbb{E}[\mathbf{x}] \right \}\left \{ \mathbf{y^T} - \mathbb{E}[\mathbf{y^T}] \right \}]\\
&= \mathbb{E}[\mathbf{xy^T}] - \mathbb{E}[\mathbf{x}]\mathbb{E}[\mathbf{y^T}]
\end{aligned}
$$

## 빈도주의와 베이지안 (Frequentist vs Bayesian)
* 빈도주의 : 반복가능한 사건들의 빈도수에 기반해서 해석
  * Ex) 0과1중 1이 나오는 신뢰구간 95% : 표본을 여러번 추출해서 생성한 다수의 신뢰구간중 95%가 1의값을 가짐
* 베이지안 : 불확실성을 정략적으로 표현
  * 베이즈 정리
    * $p(\mathbf{w})$ : 사전확률($\mathbf{w}$에 대한 사전지식)
    * $p(D|\mathbf{w})$ : 우도함수(Likeihood Function)(특정 $\mathbf{w}$값에 대해서 D의 값이 얼마나 가능성이 있는지를 나타내는 함수)
    * $p(\mathbf{w}|D)$ : D를 관찰하고 난 뒤의 $\mathbf{w}$에 대한 불확실성의 정도를 표현
    * 사후확률(조건부확률) $\propto$ 우도함수 $\times$ 사전확률
