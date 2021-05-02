---
title: Programers Level 4 도둑질
date: 2021-05-02 22:05:36
category: coding test
thumbnail: { thumbnailSrc }
draft: false
---

## **프로그래머스 Level 4 도둑질**

도둑이 어느 마을을 털 계획을 하고 있습니다. 이 마을의 모든 집들은 아래 그림과 같이 동그랗게 배치되어 있습니다.

<img align = "center" src=https://grepp-programmers.s3.amazonaws.com/files/ybm/e7dd4f51c3/a228c73d-1cbe-4d59-bb5d-833fd18d3382.png>

각 집들은 서로 인접한 집들과 방범장치가 연결되어 있기 때문에 인접한 두 집을 털면 경보가 울립니다.

각 집에 있는 돈이 담긴 배열 money가 주어질 때, 도둑이 훔칠 수 있는 돈의 최댓값을 return 하도록 solution 함수를 작성하세요.

제한사항
이 마을에 있는 집은 3개 이상 1,000,000개 이하입니다.
money 배열의 각 원소는 0 이상 1,000 이하인 정수입니다.

[문제 출처 - 프로그래머스](https://programmers.co.kr/learn/courses/30/lessons/42897)

* * *

## 풀이

이 문제는 기본적으로 원형으로 순환되는 구조지만 문제를 이것을 직선 구조로 생각하고 첫번째 집 옆에는 마지막집이 붙어있기 때문에 다음과 같이 경우를 나누어서 첫번째 집과 마지막집이 동시에 선택되지 않게 설정했다.

1. 첫번째 집을 털 경우(마지막집은 제외)
2. 첫번째 집을 털지 않을 경우

우선 이 문제를 순환하는 구조가 아닌 직선 구조로 풀게 되면 DP로 간단하게 나타낼 수 있다.   
한쪽방향으로 집을 털면서 이동하고 n번째 집을 턴다고 생각 했을 때, n번째 집까지 털 때 얻을 수 있는 최대의 돈의 양은 다음과 같은 식으로 표현이 가능하다. $dp[n]$은 $n$번째 집까지 도둑질을 했을때 최대로 얻을 수 있는 돈의 양, $m[n]$은 $n$번째 집의 돈의 양이다.

$$
dp[n] = \left\{\begin{matrix}
dp[n-2] + m[n] & if\; dp[n-1] m[n] > dp[n-2]\\ 
dp[n-1] & else
\end{matrix}\right.
$$

이는 간단하게 max 함수를 이용하여 나타낼 수 있다.

소스코드
```python
def solution(money):
    n = len(money)
    #dp 설정
    dp = [0] * n
    dp1 = [0] * n
    #첫번째 집을 털경우
    dp[0] = money[0]
    dp[1] = money[0]
    #첫번째 집을 스킵하고 두번째부터 털 경우
    dp1[0] = 0
    dp1[1] = money[1]
    for i in range(2,n-1):
        dp[i] = max(dp[i-2]+money[i], dp[i-1])
    for i in range(2,n):
        dp1[i] = max(dp1[i-2]+money[i], dp1[i-1])
    return max(dp[n-2],dp1[n-1])
```