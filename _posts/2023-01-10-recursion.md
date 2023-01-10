---
layout: single
title: "[Data Structure] Recursion(제귀)"
categories: "자료구조"
toc: true
# sidebar:
#   nav: "docs"
---

제귀는 **알고리즘이나 함수가 자기 자신을 호출하여 주어진 문제를 해결하는 기법**이다. 알고리즘이 제귀적으로 되어 있는 경우인 **팩토리얼 함수 계산, 피보나치 수열, 이항계수 계산, 이진 트리 알고리즘, 이진 탐색, 하노이 탑 문제**에 주로 쓰인다.

## 제귀 호출

- 기본적으로 제귀는 **다른 함수를 호출하는 것과 동일**

- 복귀주소가 시스템 스택에 저장되며, 호출되는 함수를 위한 매개 변수와 지역 변수를 스택으로부터 할당

- 함수를 위한 시스템 스택의 공간은 **활성 레코드(activation record)**

- 활성 레코드가 없으면 함수호출마다 새로운 지역변수를 만들지 못하므로, 제귀를 만들 수 없음. 따라서 **COBOL, FORTRAN은 제귀 불가**

- 한편, 제귀로 구성할 수 있는 알고리즘은 반복으로도 구성할 수 있음. 단, 제귀가 반복보다 반드시 유리한 것은 아니며 오히려 불리할 수도 있음

### 피보나치 수열 제귀(제귀 시간 복잡도 > 반복 시간 복잡도)

```python
def fibo(n):
  if n == 0:
    return 0
  elif n == 1:
    return 1
  else:
    return fibo(n-1) + fibo(n-2)
```

`fibo(4)`의 경우

1. `fibo(4) = fibo(3) + fibo(2)`

2. 이 때, `fibo(3)`이 먼저 실행. `fibo(3) = fibo(2) + 1`/ 이때 `fibo(1)`이 시스템 스택에 쌓이나 리턴

3. `fibo(2)` 실행, `fibo(2) = 0 + 1`/ 이때 `fibo(0)`과 `fibo(1)`이 시스템 스택에 쌓이나 리턴됨.

4. `fibo(3)`으로 돌아오고, `fibo(3) = 2`

5. `fibo(4)`로 돌아오고, `2 + fibo(2)`에서 `fibo(2)` 실행

6. 3의 절차 수행.

7. `fibo(4) = 2 + 1`로 반환됨

8. 피보나치 수열의 경우, 제귀로 구현한 시간 복잡도는 O(2<sup>n</sup>)이지만 반복으로 구현한 시간 복잡도는 O(n)으로 반복으로 구현하는 것이 유리

### 거듭제곱 제귀(제귀 시간 복잡도 < 반복 시간 복잡도)

```python
def power(x, n):
  if n == 0:
    return 1
  else:
    if x % 2:
      return x * power(x**2, (n-1)/2)
    else:
      return power(x**2, n/2)
```

`power(2, 5)`의 경우

1. `power(2, 5) = 2 * power(4, 2)`

2. `power(4, 2)` 호출, `power(4, 2) = power(16, 1)`

3. `power(16, 1)` 호출, `power(16, 1) = 16 * power(256, 0)`

4. `power(256, 0)` 호출, `power(256, 0) = 1`이므로 1 반환

5. `power(16, 1) = 16 * 1`이므로 16 반환

6. `power(4, 2) = power(16, 1)`이므로 16 반환

7. `power(2, 5) = 2 * 16`이므로 32 반환

8. 거듭제곱의 경우, 주어진 문제를 더 작은 동일한 문제로 분리하는 기법인 분할정복이 가능함. 제귀로 구현한 시간복잡도는 O(log<sub>2</sub>n)이나 반복으로 구현한 시간복잡도는 O(n)

### 하노이탑 문제

- 조건

  1. 한 번에 하나의 원판만 이동

  2. 맨 위에 있는 원판만 이동 가능

  3. 크기가 작은 원판 위에 큰 원판이 쌓일 수 없음

  4. 중간의 막대는 이용 가능하나, 조건 준수

- 풀이방법

  1. start에 있는 n-1개의 원판을 tmp로 옮긴다

  2. start에 있는 마지막 원판을 end로 옮긴다.

  3. tmp에 있는 n-1개의 원판을 start로 옮긴다.

- 풀이코드
  ```python
  def hanoi(n, start, tmp, end):
    if n == 1:
      print(f'원판 {n}이 {start}에서 {end}로 이동')
    else:
      hanoi(n-1, start, end, tmp)
      print(f'원판 {n}이 {start}에서 {end}로 이동')
      hanoi(n-1, tmp, start, end)
  ```
- 하노이탑의 총 이동 횟수는 **2<sup>n</sup>-1**

### 예시문제

[백준 2747 피보나치 수](https://www.acmicpc.net/problem/2747)

[백준 2748 피보나치 수 2](https://www.acmicpc.net/problem/2748)

[백준 10826 피보나치 수 4](https://www.acmicpc.net/problem/10826)

[백준 10870 피보나치 수 5](https://www.acmicpc.net/problem/10870)

[백준 10870 피보나치 수 5](https://www.acmicpc.net/problem/10870)

[백준 1914 하노이탑](https://www.acmicpc.net/problem/1914)

[백준 1914 하노이탑 이동순서](https://www.acmicpc.net/problem/11729)
