---
layout: single
title: "[Algorithm] DFS/BFS 사전 지식 정리 (Stack, Queue)"
categories: "Algo"
toc: true
# sidebar:
#   nav: "docs"
---

이번 정리는 많은 양의 데이터 중에서 원하는 데이터를 찾는 과정인 탐색에 관련된 알고리즘인
**DFS, BFS**에 서전지식에 관한 것이다. 선형 자료구조에 해당하는 **Stack**, **Queue**에 관해 이야기하고자 한다.

## Stack

- 선형 자료구조로, **First in, Last out(선입후출)이므로 LIFO**

- 마지막에 입력된 것이 처음으로 출력되는 데이터 저장 방식

- python의 경우 **list**로 쉽게 구현할 수 있음

### Stack 예시 코드

문제링크 : 스택[https://www.acmicpc.net/problem/10826](https://www.acmicpc.net/problem/10826)

```python
import sys
N = int(input())

stack = []
for i in range(N):
    list1 = list(map(str, sys.stdin.readline().split()))
    if len(list1) > 1:
        stack.append(int(list1[1]))
    else:
        if list1[0] == 'top':
            if len(stack) == 0:
                print(-1)
            else:
                print(stack[-1])
        elif list1[0] == 'size':
            print(len(stack))
        elif list1[0] == 'empty':
            if len(stack) == 0:
                print(1)
            else:
                print(0)
        else:
            if len(stack) == 0:
                print(-1)
            else:
                print(stack.pop())

```

- `stack.append(x)`를 통해 스택의 top에 데이터를 계속 쌓을 수 있으며

- `stack.pop()`을 통해 스택의 top에 있는 데이터를 반환할 수 있음

- `stack.pop(index)`로 사용할 수 있으나, 이는 index에 해당하는 데이터를 삭제 후 리스트의 원소 위치를 조정해야 하므로 시간복잡도가 증가하므로 지양하는게 좋음

### Stack 관련 문제 예시

[백준 1874 스택수열](https://www.acmicpc.net/problem/1874)

[백준 9012 괄호](https://www.acmicpc.net/problem/9012)

## Queue

- 기본적으로는 선형 자료구조로, **First in, First out(선입선출)이므로 FIFO**

- 처음 입력한 값이 처음으로 출력되는 자료구조

- python의 경우 **deque**로 쉽게 구현할 수 있음

### Queue 예시 코드

문제링크 : 큐[https://www.acmicpc.net/problem/10845](https://www.acmicpc.net/problem/10845)

```python
import sys
from collections import deque
N = int(input())

stack = deque()
for i in range(N):
    list1 = list(map(str, sys.stdin.readline().split()))
    if len(list1) > 1:
        stack.append(int(list1[1]))
    else:

        if list1[0] == 'back':
            if len(stack) == 0:
                print(-1)
            else:
                print(stack[-1])
        elif list1[0] == 'size':
            print(len(stack))
        elif list1[0] == 'empty':
            if len(stack) == 0:
                print(1)
            else:
                print(0)
        elif list1[0] == 'pop':
            if len(stack) == 0:
                print(-1)
            else:
                print(stack.popleft())
        elif list1[0] == 'front':
            if len(stack) == 0:
                print(-1)
            else:
                print(stack[0])




```

- `deque.append(x)`를 통해 데이터를 쌓을 수 있는 것은 동일하나, `deque.appendleft(x)`도 지원하므로 왼쪽, 오른쪽 모두 데이터를 쌓을 수 있음

- `stack.popleft()`을 처음 입력한 데이터를 반환할 수 있음

### Queue 관련 문제 예시

[백준 11866 요세푸스 문제 0](https://www.acmicpc.net/problem/11866)

[백준 5464 주차장](https://www.acmicpc.net/problem/5464)
