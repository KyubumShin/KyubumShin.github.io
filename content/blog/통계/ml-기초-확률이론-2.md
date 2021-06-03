---
title: ML 기초 - 확률이론 2
date: 2021-05-31 21:05:16
category: 통계
thumbnail: { thumbnailSrc }
draft: false
---
# 확률이론
* 먼저 간단하게 포스팅하고 추후에 추가적인 내용을 넣을예정
## 정규분포(Gaussian Distribution)
### 단일변수 x 를 위한 정규분포(가우시안 분포)
$$
N(x|\mu,\sigma^2) = \frac{1}{(2\pi\sigma^2)^{1/2}}exp\left \{ -\frac{1}{2\sigma^2}(x-\mu)^2\right \} \\
$$

### 기대값(Expectation) : 확률변수 * 밀도함수
$$
\begin{aligned}
\mathbb{E}[x] &= \int_{-\infty}^{\infty} N(x|\mu,\sigma^2)xdx \\ 
&= \mu
\end{aligned}
$$

### 분산(Variance) :
* $\frac{d}{dy}\int_{-\infty}{\inf}N(x|\mu,y)dx = 0$ 를 이용하여 다음을 증명(생략)
$$
\begin{aligned}
var[x] &= \int_{-\infty}^{\infty} (x-\mu)^2N(x|\mu,\sigma^2)xdx \\
&= \sigma^2
\end{aligned}
$$

### 최대우도해(Maximum Likeihood solution):
* $\mathbf{X} = (x_1,...,x_N)^T$가 독립적으로 같은 가우시안 붙포로부터 추출된 N개의 샘플들이라고 할때 각각의 확률값의 곱과 같다.
$$
p(\mathbf{X}|\mu,\sigma^2) = p(x_1,...,x_N|\mu,\sigma^2) = \prod_{n=1}^{N}N(x_n|\mu,\sigma^2) \\
\ln p(\mathbf{X}|\mu,\sigma^2) = -\frac{1}{2\sigma^2}\sum_{n=1}{N}(x_n - \mu)^2 - \frac{N}{2}\ln\sigma^2 - \frac{N}{2}\ln(2\pi)
$$
여기서 log함수는 단조증가함수이므로 1번식이나 2번식이 최대값을 가지게하는 파라미터의 값은 동일하다. 그래서 2번식을 각각의 파라미터에 대해 편미분하고 그 값이 0이되도록 하는 파라미터를 찾는 과정을 통해서 우도함수(Likeihood Function)을 최대로 할 수 있다.

* 최대우도를 만들어주는 $\mu$의 값
$$
\hat{\mu} = \frac{1}{N}\sum_{n=1}^{N}x_n
$$

* 최대우도를 만들어 주는 $\sigma$의 값
$$
\hat{\sigma^2} = \frac{1}{N}\sum_{n=1}^{N}(x_n - \mu)^2
$$

# 참고
1. 최대우도법 / https://angeloyeo.github.io/2020/07/17/MLE.html