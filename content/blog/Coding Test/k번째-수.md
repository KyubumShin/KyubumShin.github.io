---
title: K번째 수
date: 2021-05-03 14:05:82
category: coding test
thumbnail: { thumbnailSrc }
draft: false
---

## **프로그래머스 Level 2 K번째수**

배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

제한사항
* array의 길이는 1 이상 100 이하입니다.
* array의 각 원소는 1 이상 100 이하입니다.
* commands의 길이는 1 이상 50 이하입니다.
* commands의 각 원소는 길이가 3입니다.

[문제 출처 - 프로그래머스](https://programmers.co.kr/learn/courses/30/lessons/42748)


* * *
## 풀이
어렵게 생각할것은 없다. 리스트를 자르고 sort()하고 n번째 인덱스의 수를 꺼내서 추가해주면 된다.

```python
def solution(array, commands):
    answer = []
    for i in commands:
        temp = array[i[0]-1:i[1]]
        temp.sort()
        answer.append(temp[i[2]-1])
    return answer
```

아래의 코드는 List Comprehension 이용하여 파이써닉하게 푼 코드 위와 과정은 똑같다
```python
def solution(array, commands):
    return [sorted(array[i[0]-1:i[1]])[i[2]-1] for i in commands]
```
