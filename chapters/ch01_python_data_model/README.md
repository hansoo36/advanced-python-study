# Chapter 1: 파이썬 데이터 모델

> 학습 기간: 2026-01-05 ~

## 📌 핵심 개념
데이터 모델
- 파이썬을 설명하는 일종의 프레임워크  
- Sequence/Iterator/Function/Co-routine/Class/Context 등 언어 자체를 구성하는 단위 간 인터페이스를 공식적으로 정의  
- 파이썬을 통해 정의한 객체를 컬렉션, 함수 호출, 문자열 표현 등의 기능과 결합하려면 해당하는 메서드 구현이 필요

## 🎯 주요 내용

### 1. \_\_getitem\_\_()과 \_\_len\_\_() 예시
- 카드 덱을 클래스를 이용해 구현하여 \_\_getitem\_\_()과 \_\_len\_\_() 예시를 보여준다.

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
