# Chapter 2: 시퀀스의 배열

> 학습 기간: 2026-01-11 ~

## 📌 핵심 개념
- 지능형 리스트(list comprehension: listcomp)와 제너레이터 표현식(generator expression: genexp) 활용
- Tuple을 Record로 사용할때와 Immutable List로 사용할 때의 차이점
- Sequence Unpacking과 Pattern
- Slicing, Array, Queue

## 🎯 주요 내용

### 1. 내장 시퀀스 개요
- 자료형에 따른 구분
  - Container Sequence (컨테이너형)
    - list, tuple, collections.deque
    - 객체에 대한 참조를 담으며, 어떠한 자료형도 가능함 
  - Flat Sequence (균일형)
    - str, bytes, array.array
    - 객체에 대한 참조 대신 자신의 메모리 공간에 각 항목의 값을 직접 담음
    - 메모리를 더 적게 사용하지만, 기본적인 자료형만 담을 수 있음

- 가변성에 따른 구분
  - 가변: list, bytearray, array.array, collections.deque
  - 불변: tuple, str, bytes

## 💡 코드 예제
```python
# For문 사용 시
symbols = '$₵₤¥€¤'
codes = []
for symbol in symbols:
    codes.append(ord(symbol))
print(codes)

# listcomp 사용 시
symbols = '$₵₤¥€¤'
codes = [ord(symbol) for symbol in symbols]
print(codes)

```

```
[36, 8373, 8356, 165, 8364, 164]
[36, 8373, 8356, 165, 8364, 164]
```

(Note)
- 해당 예제에서는 명확한 의도를 표현한 listcomp를 사용하는 것이 좋다.
- 생성된 리스트를 사용하지 않을거라면 listcomp 구문을 사용할 필요가 없다.
- listcomp 구문이 두 줄을 넘어간다면 코드를 분할하거나 For문을 사용하는 편이 더 나을 수 있다.

## 🔍 Deep Dive

- Walrus Operator (:=)
  - 바다코끼리 연산자: Assign과 Return을 동시에 진행함
 
```python
# 기존 방식
filtered_data = []
for item in data:
	result = process(item)
    if result > 0:
    	filtered_data.append(result)

# Walrus Operator 적용
filtered_data = [result for item in data if (result := process(item) > 0]
```

```python
x = 'ABC'
codes = [ord(x) for x in x]
print(x)
print(codes)

codes = [last := ord(c) for c in x]
print(last)
print(c)
```

```
'ABC'
[65, 66, 67]

67
Traceback (most recent call last):
	File "<stdin>", line 1, in <module>
NameError: name 'c' is not defined
```

## 🚀 실전 활용

<!-- 실무에서 어떻게 적용할 수 있을지 -->

## 🤔 생각 & 질문

- [ ] 더 알아볼 것
- [ ] 시도해볼 것

## 📚 참고 자료


## 🏷️ Tags
`#python` `#fluent-python` `#data-model` `#special-methods`
