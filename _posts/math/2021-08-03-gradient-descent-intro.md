---
title: "Gradient Descent (경사하강법) Intro"
categories:
  - Calculus
tags:
  - calculas
  - gradient_descent
  - 
last_modified_at: 2021-08-03T00:00:00-00:00
---


## Summary 🤙
---
Gradient Descent (경사하강법)를 통해 함수 f의 극소값에 도달할 수 있다.


## Index 👀       
  * [Why](#why)
  * [Definition](#definition)
  * [Feature](#feature)
  * [Use Cases](#use-cases)
  * [Related](#related)
  * [Implementation](#implementation)

## Why 🤷
---
기계 학습에서 주로 사용되는 패턴은 특정 함수를 최소화하기 위해 반복적인 계산을 수행하는 것이다. Linear Regression을 위해 Loss함수를 최소화 하는 것이 대표적인 예이다. 
또한 Gradient Descent는 모든 차원과 공간에서 적용이 가능하다. 



## Definition 🧑‍🏫
---
변수 $x$에 대해 $f(x)$의 극솟값은 $f(x_k-f'(x_k))$가 0이 될 때까지 반복적으로 수행하면 도달할 수 있다.


## Feature 👍
---
TODO 


## Use Cases 🪢
---
TODO  


## Related 🧶
---
TODO 


## Implementation 😎
---
```python
# 1차원
import sympy as sym
from sympy.abc import x

f = sym.poly(x**2 + 2*x + 3)

val = init_value
grad = sym.diff(f)
```