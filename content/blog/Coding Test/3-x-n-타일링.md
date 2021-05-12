---
title: 3 x n 타일링
date: 2021-05-07 23:05:71
category: coding test
thumbnail: { thumbnailSrc }
draft: false
---

## **프로그래머스 Level4 3 x n 타일링**

가로 길이가 2이고 세로의 길이가 1인 직사각형 모양의 타일이 있습니다. 이 직사각형 타일을 이용하여 세로의 길이가 3이고 가로의 길이가 n인 바닥을 가득 채우려고 합니다. 타일을 채울 때는 다음과 같이 2가지 방법이 있습니다

* 타일을 가로로 배치 하는 경우
* 타일을 세로로 배치 하는 경우
예를들어서 n이 8인 직사각형은 다음과 같이 채울 수 있습니다.

![](https://i.imgur.com/zBW7peI.png)

직사각형의 가로의 길이 n이 매개변수로 주어질 때, 이 직사각형을 채우는 방법의 수를 return 하는 solution 함수를 완성해주세요.

제한사항
* 가로의 길이 n은 5,000이하의 자연수 입니다.
* 경우의 수가 많아 질 수 있으므로, 경우의 수를 1,000,000,007으로 나눈 나머지를 return해주세요.

[문제 출처 - 프로그래머스](https://programmers.co.kr/learn/courses/30/lessons/12902)

* * *
## 풀이
$n = 6$ 일때 까지 계산해서 점화식으로 풀어보니
$$ dp_{n} = 4dp_{n-1} - dp_{n-2}$$
가 나왔다

```python
def solution(n):
    if n%2 == 1:
        return 0
    dp = [0] * (n//2 +1)
    dp[0] = 1
    dp[1] = 3
    for i in range(2,n//2+1):
        dp[i] = dp[i-1]*4 -dp[i-2]
    return dp[n//2] % 1000000007
```
