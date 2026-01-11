# Chapter 1: 파이썬 데이터 모델

> 학습 기간: 2026-01-05 ~ 2026-01-07

## 📌 핵심 개념
데이터 모델
- 파이썬을 설명하는 일종의 프레임워크  
- Sequence/Iterator/Function/Co-routine/Class/Context 등 언어 자체를 구성하는 단위 간 인터페이스를 공식적으로 정의  
- 파이썬을 통해 정의한 객체를 컬렉션, 함수 호출, 문자열 표현 등의 기능과 결합하려면 해당하는 메서드 구현이 필요

## 🎯 주요 내용

### 1. `__getitem__`()과 `__len__`() 예시
- 카드 덱을 클래스를 이용해 구현하여 `__getitem__`()과 `__len__`() 예시를 보여준다.

## 💡 코드 예제
```python
import collections

Card = collections.namedtuple('Card', ['rank', 'suit'])

class FrenchDeck:
    ranks = [str(n) for n in range(2, 11)] + list('JQKA')
    suits = 'spades diamonds clubs hearts'.spliit()

    def __init__(self):
        self._cards = [Card(rank, suit) for suit in self.suits
                                        for rank in self.ranks]
    def __len__(self):
        return len(self._cards)

    def __getitem__(self, position):
        return self._cards[position]


beer_card = Card('7', 'diamonds')
print(beer_card)

deck = FrenchDeck()
print(len(deck))

print(deck[0])
```

```
Card(rank='7', suit='diamonds')
52
Card(rank='2', suit='spades')
```

### 2. Vector
- Vector의 덧셈 연산자와 곱셈 연산자를 `__repr__`(), `__abs__`(), `__add__`(), `__mul__`() 로 구현한 예시를 보여준다.

## 💡 코드 예제
```python
import math

class Vector:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __repr__(self):
        return f'Vector({self.x!r}, {self.y!r})'

    def __abs__(self):
        return math.hypot(self.x, self.y)

    def __bool__(self):
        return bool(abs(self))

    def __add__(self, other):
        x = self.x + other.x
        y = self.y + other.y
        return Vector(x, y)

    def __mul__(self, scalar):
        return Vector(self.x * scalar, self.y * scalar)


v1 = Vector(2, 4)
v2 = Vector(2, 1)
print(v1 + v2)

v = Vector(3, 4)
print(abs(v))

print(v * 3)
print(abs(v * 3))
```

```
Vector(4, 5)
5.0
Vector(9, 12)
15.0
```

### 3. 사용자 정의형의 Boolean값

| Operation | Result | Notes |  
| --- | --- | --- |  
| `x or y` | If x is true, then x, else y | It only evaluates the second argument if the first one is false <sup>1) |  
| `x and y` | If x is false, then x, else y | It only evaluates the second argument if the first one is true <sup>1) |  
| `not x` | If x is false, then `True`, else `False` | `not` has a lower priority than non-Boolean operators <sup>2) |  

1) Short-circuit evaluation: Second operands is only evaluated if the first operand is insufficientto determine the outcome of the entire expression
(Ex) `False and ...` results in False. The part after `and` is never checked
2) `not a == b` is interpreted as `not (a == b)`, and `a == not b` is a syntax error  

- `len()`을 메서드로 만들지 않는 이유는, `abs()`와 마찬가지로 파이썬 데이터 모델의 특별 대우를 받기 때문 → 효율적인 실행을 위해


## 🔍 Deep Dive

<!-- 책에 없지만 추가로 탐구한 내용 -->
<!-- 궁금했던 점과 찾아본 내용 -->

## 🚀 실전 활용

<!-- 실무에서 어떻게 적용할 수 있을지 -->

## 🤔 생각 & 질문

- [ ] 더 알아볼 것
- [ ] 시도해볼 것

## 📚 참고 자료


## 🏷️ Tags
`#python` `#fluent-python` `#data-model` `#special-methods`
