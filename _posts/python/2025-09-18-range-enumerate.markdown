---
layout: post
title: "range, enumerate"
date: 2025-09-18 09:53:00 +0900
categories: 
  - Dev
  - python
tag: python
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## range 함수

`range([start,] stop [,step])`

필요한 만큼의 숫자를 만들어내는 유용한 기능이다. for문과 함께 주자 사용되는 함수이다.
이 함수는 입력받은 숫자에 해당되는 범위의 값을 반복 가능한 객체로 만들어 리턴한다.

```python
# range 함수
# range(stop) : 0 ~ stop-1 까지의 정수
print(range(5), type(range(5)))
print(tuple(range(5)))
print(set(range(5)))
print(list(range(5)))

for i in range(5):
    print(i, end=' ')
print()

# range(start,stop) : start ~ stop-1 까지의 정수
print(list(range(5, 10)))

# range(start,stop, step) : start 부터 step 씩 증감하며 stop-1 까지의 정수
print(list(range(2, 11, 2)))
print(list(range(1, 11, 2)))
print(list(range(9, 0, -2)))
print(list(range(10, 0, -2)))
```

**실행 결과**

```bash
range(0, 5) <class 'range'>
(0, 1, 2, 3, 4)
{0, 1, 2, 3, 4}
[0, 1, 2, 3, 4]
0 1 2 3 4 
[5, 6, 7, 8, 9]
[2, 4, 6, 8, 10]
[1, 3, 5, 7, 9]
[9, 7, 5, 3, 1]
[10, 8, 6, 4, 2]
```


## enumerate 함수

- 리스트가 있는 경우 순서와 리스트의 값을 전달하는 기능을 가진다.
- enumerate는 "열거하다"라는 뜻이다.
- 이 함수는 순서가 있는 자료형(list, set, tuple, dictionary, string)을 입력받아 인덱스 값을 포함하는 enumerate 객체를 리턴한다.
- 보통 enumerate 함수는 for문과 함께 자주 사용된다.

```python
# enumerate 함수
data = enumerate((1, 2, 3))
print(data, type(data))

for i, value in data:
    print(i, ":", value)
print()

data = enumerate({1, 2, 3})
for i, value in data:
    print(i, ":", value)
print()

data = enumerate([1, 2, 3])
for i, value in data:
    print(i, ":", value)
print()

dict1 = {'이름': '한사람', '나이': 33}
data = enumerate(dict1)
for i, key in data:
    print(i, ":", key, dict1[key])
print()

data = enumerate("재미있는 파이썬")
for i, value in data:
    print(i, ":", value)
print()
```


**실행 결과**

```bash
<enumerate object at 0x0000000002424EA0> <class 'enumerate'>
0 : 1
1 : 2
2 : 3

0 : 1
1 : 2
2 : 3

0 : 1
1 : 2
2 : 3

0 : 이름 한사람
1 : 나이 33

0 : 재
1 : 미
2 : 있
3 : 는
4 :  
5 : 파
6 : 이
7 : 썬
```


> 출처: [https://wikidocs.net/20792](https://wikidocs.net/20792)