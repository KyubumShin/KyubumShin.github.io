---
title: ml 기초 - 결정이론1
date: 2021-06-01 18:06:32
category: 통계
thumbnail: { thumbnailSrc }
draft: false
---

# 결정이론
## 결정이론이란?
* 새로운 데이터$x$가 주어질때 확률모델 $p(\mathbf{x}, \mathbf{t})$에 기반해 최적의 결정을 내리는 이론
  * 추론단계 : 결합확률분포 $p(\mathbf{x},C_k)$를 구하는것
  * 결정단계 : 상황에 대해 확률이 주어졌을 때 어떤 방식으로 최적의 결정을 내릴 것인지를 정하는 단계
* $p(C_k|\mathbf{x})$ 값을 알면 $p(\mathbf{x},C_k)$또한 구할 수 있음

$$
p(\mathbf{x}|C_k) = \frac{p(C_k|\mathbf{x})p(\mathbf{x})}{p(C_k)}
$$

* $p(C_k|\mathbf{x})$ 를 최대화시키는 k를 구하는것이 좋은결정 > 최대우도법을 사용?

## 결정이론 - 이진분류
<br></br>
<p align="center"><img src="./missclass.png"></p>  

* 결정영역 (decision region)
  * 어떤 값이 특정 범위 안에 있으면 $C_i$로 분류되는 영역 $R_i$
  * $R_i = \left \{ x : pred(x) = C_i \right \}$
  * ex) $x$ 가 $R_1$의 범위안에 존재하면 $C_1$로 분류
* 분류 오류 확률
  * $R_1$에서 $C_2$로 분류될 확률 + $R_2$에서 $C_1$으로 분류될 확률
$$
\begin{aligned}
p(miss) &= p(x \in R_1,C_2) + p(x \in R_2,C_1)\\
&= \int_{R_1}p(x,C_2) + \int_{R_2}p(x,C_1)dx
\end{aligned}
$$