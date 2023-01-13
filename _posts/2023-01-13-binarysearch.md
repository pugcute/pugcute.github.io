---
layout: single
title: "[Algorithm] 이진 탐색(binary search)"
categories: "Algo"
toc: true
# sidebar:
#   nav: "docs"
---

이번 정리는 탐색에 관한 것이다. 순차탐색은 **데이터를 찾기 위해 앞에서부터 데이터를 하나씩 찾는 것**을 의미한다. 이는 `for`와 같은 반복문으로 쉽게 구현할 수 있으나 시간이 많이 걸린다는 단점이 있다. 이에 반해 이진탐색은 **정렬된 리스트라는 제약조건에서 사용할 수 있지만 검색범위를 줄이면서 데이터를 검색**하는 기법이다.

## 이진탐색

- 제약조건은 **데이터가 미리 정렬되어 있어야 하는 것**

- 탐색하고자 하는 범위의 `start, end, mid`를 설정하고, 찾는 데이터와 `mid`를 끊임없이 비교한다

- 시간복잡도는 **O(N)**

- 제귀와 반복으로 구현 가능함.

- 제귀

  ```python
  def binary_search(target, start, end):
      if start > end:
          return None
      mid = (start + end) // 2
      if moneys[mid] == target:
          return mid
      elif moneys[mid] > target:
          return binary_search(target, start,  mid-1)
      else:
          return binary_search(target, mid+1, end)

  moneys = [120, 110, 140, 150]
  moneys.sort()
  print(binary_search(140, 0, len(moneys)))v
  ```

- 반복

  ```
  moneys = [120, 110, 140, 150]
  moneys.sort()

  start = 0
  end = len(moneys)-1

  while start <= end:
      if start > end:
          break
      mid = (start + end) // 2

      if moneys[mid] > 150:
          end = mid - 1
      else:
          start = mid + 1
          answer = mid
  ```

### 예시문제

[백준 1654 랜선자르기](https://www.acmicpc.net/problem/1654)

[백준 1805 나무자르기](https://www.acmicpc.net/problem/1805)

[백준 2512 예산](https://www.acmicpc.net/problem/2512)
