# C style과 다른 python만의 독특한 문법들

## Unpacking

### iterable

- 리스트, 튜플, 문자열 등 모든 반복 가능한 객체를 iterable 하다고 한다.
- 이런 객체는 모두 사용가능.

```
a, b = map(int, input().split())
```

> 입력 받은 list에서 첫번째, 마지막 값 또는 첫번째, 마지막 값만 제외하고 싶을 땐?

```
_list = [1, 2, 3, 4, 5]
first_index, *rest, last_index = _list
print(rest) # 2 3 4
```

파이썬은 가변인자\*(asterisk)를 다음과 같은 상황에 사용한다.

- 곱셈, 거듭제곱
- List형 컨테이너를 반복해서 확장
- 가변 인자
- Unpacking

즉, 인자의 갯수가 몇개가 될지 확실하지 않을때 사용.
first_index와 last_index가 앞과 끝을 가져가면, rest가 나머지를 가져간다.

### Unpacking은 ?

```
_list = [1, 2, 3, 4, 5]
for num in _list:
    print(num, end = ' ') # 1 2 3 4 5
```

\_list내 원소들을 출력

```
_list = [1, 2, 3, 4, 5]
print(*_list) # 1 2 3 4 5
```

동일한 결과 -> 이것이 **List Unpacking**

list외에도 튜플, set 등 컨테이너형 구조에선 모두 적용가능

### Packing

```
a, b, c = [1, 2, 3]
d = a, b, c
print(d) # (1, 2, 3)
```

- 하나의 변수에 여러 값을 할당하게 되면 튜플로 묶인다.

---

## List Comprehension (지능형 리스트)

```
_list = [i for i in range(10)] # 0 1 2 3 4 5 6 7 8 9
```

- List Comprehension 아래와 같은 구조이다.

> (변수를 활용해 만들 값) for (변수 명) in (순회할 수 있는 값)

그러므로 List Comprehension으로 된 코드는, for 뒤 부터 읽으면 된다.

```
## 백준 온라인 저지 1920번 "수 찾기" (<http://boj.kr/1920>)
import sys
input = sys.stdin.readline

_ = input()
_set = set(map(int, input().split()))
q = input()
_list = list(map(int, input().split()))

print(*[1 if dt in _set else 0 for dt in _list], sep = '\\n')
```

\_list에 있는 원소를 dt라고 하고, 앞에 있는 `1 if dt in _set else 0`에 대입한다는 의미.

해당 내용은 \_set에 원소가 들어있으면 1, 아니면 0을 리턴해라.

### 다차원 배열도 사용가능

```
square = [[x ** 2 for x in range(3)] for _ in range(3)]
print(square) # [[1, 4, 9], [1, 4, 9], [1, 4, 9]]
```

코드의 길이를 확실히 줄일 수 있다는 장점
but 너무 길면 가독성 해치므로 사용하지 말 것

```
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print([[x for x in row if x % 3 == 0] for row in matrix if sum(row) >= 10]) # [[6], [9]]
```

리스트 뿐만이 아니라 tuple, set, dict도 만들 수 있고
dict의 경우 뒷 부분에서 zip을 배우고 나면 자주 쓰일 수 있다.

추가 예제

```
# 1 ~ 10을 담는 리스트를 만들기.
_list = [i for i in range(10)]

# 2, 4, 6, ..., 20을 담는 리스트를 만들기.
_list = [2 * i for i in range(10)]

# 주어진 리스트를 받아 3의 배수만 담는 리스트를 만들기.
tmp = [random.randrange(1, 200) for i in range(100)]
_list = [i for i in tmp if i % 3 == 0]

# 값이 두개 들어있는 튜플을 받아 리스트를 생성하되, 튜플 내부의 값을 뒤집어서 저장.
list_of_tupel = [(i, j) for i in range(100), for j in range(100, 0, -1)]
_list = [(j, i) for i, j in list_of_tuple]

# 주어진 리스트를 그대로 담되, 15가 넘어가는 값은 15로 바꿔서 저장.
_list = [i if i <= 15 else 15 for i in tmp]

# 두 개의 리스트를 합치되, 가능한 모든 조합을 저장하는 리스트를 만들기.
x = [i for i in range(5)]
y = [i for i in range(5)]
_list = [(i, j) for i in x, for j in y]
```

### if

- 앞에 붙는 if는 삼항 연산자의 if
  (즉, 값이 앞 조건을 만족하면 어떤 값, 만족하지 못하면 다른 값)
- 맨 끝에 붙는 if는 값을 넣을지, 뺄지 결정하는 조건

---

## Dictionary 잘 쓰기

Dictionary와 Set 어디에 어떻게 사용하면 좋은 지 ?

Dictionary와 Set은 _Hash Table_ 구조를 띄고 있습니다. 그래서 삽입, 삭제, 탐색 연산의 시간복잡도는 O(1)

- 가장 많이하는 실수 **값을 찾기 위해 list에서 in을 사용한다는 것**

```
#데이터 순차적으로 탐색
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for i in range(100):
    if i in data:
        print(1)
#하나의 숫자를 찾기 위해 최대 10번 데이터를 확인
```

### SET

데이터양이 많아질수록 시간이 많이 소요됨. 이럴땐 set을 사용해야한다.

```
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
_data_set = set(data)

for i in range(100):
    if i in data:
        print(1)
```

set의 구조상, 같은 값이 들어올 수 없기 때문에 시간 절약해줌

```
i_want_to_erase_duplicate_element = [21, 31, 65, 21, 58, 94, 13, 31, 58]
completed_list = list(set(i_want_to_erase_duplicate_element)) # 21, 31, 65, 58, 94, 13

test_list = ['Test', 'test', 'TEST', 'tteesstt']
converted_list = list(set(map(lambda string: string.lower(), test_list))) # test, tteesstt
```

set은 iterable한 데이터를 기반으로 만들 수 있으니, 그걸 다시 list로 바꿔주면 중복된 값이 제거된 list가 만들어진다.

아래 코드는 조금 어려울텐데, 우리는 lambda를 **익명 함수**라고 합니다.
뒤에 있는 `string`은 각각의 값을 string이라고 지칭하겠다고 선언.
즉, 각각의 데이터를 소문자로 바꾸고, 그걸 set으로 바꾸고, 다시 list로 돌림

### DICTIONARY

dictionary는 키와 쌍으로 이루어져 있다.

```
fruit = ['apple', 'grape', 'orange', 'banana']
price = [3200, 15200, 9800, 5000]
_dict = {}

for i in range(len(price)):
    _dict.append((fruit[i], price[i])) # {'apple' : 3200, 'grape' : 15200, 'orange' : 9000, 'banana' : 5000}
```

이렇게 생성할까?

### **zip**

- 각 iterables 의 요소들을 모으는 이터레이터를 만듭니다.

즉, 리스트를 묶어준다. zip은 다양하게 활용가능이지만, dictionary를 만들 때도 유용.

```
fruit = ['apple', 'grape', 'orange', 'banana']
price = [3200, 15200, 9800, 5000]

_dict = dict(zip(fruit, price)) # {'apple' : 3200, 'grape' : 15200, 'orange' : 9000, 'banana' : 5000}
```

일반적으로 딕셔너리에서 없는 값을 찾으려고 하면, 오류가 납니다.

```
fruit = ['apple', 'grape', 'orange', 'banana']
price = [3200, 15200, 9800, 5000]
_dict = dict(zip(fruit, price))

print(_dict['strawberry']) # Error!
```

오류를 피하기 위해 in 옵션을 사용(데이터가 있는지 확인 & 없으면 값 추가 & 있으면 출력)

그런데, 꼭 if를 써야 할까?

```
fruit = ['apple', 'grape', 'orange', 'banana']
price = [3200, 15200, 9800, 5000]
_dict = dict(zip(fruit, price))

print(_dict.setdefault('strawberry', 0)) # 0
```

### `setdefault`

- 딕셔너리에 값이 있을 땐 해당 값을 리턴
- 값이 없을 땐 두번째 인자로 넘겨준 값을 추가하고 추가한 값을 리턴

### **defaultdict**

- 위의 메소드를 활용한 _유사_ dictionary

```
from collections import defaultdict

movie_review = [('Train to Busan', 4), ('Clementine', 5), ('Parasite', 4.5), ('Train to Busan', 4.2), ('Train to Busan', 4.5), ('Clementine', 5)]

index = defaultdict(list)

for review in movie_review:
    index[review[0]].append(review[1]) # {'Train to Busan': [4, 4.2, 4.5], 'Clementine': [5, 5], 'Parasite': [4.5]}
```

defaultdict 에서 값을 검색할 때, 값이 없으면 인자로 넘겨준 값이 default 값이 됨
결국 찾을 때 마다 setdefault를 암묵적으로 실행해준 것

### DICTIONARY unpacking 하기

unpacking에서 list, tuple에서 사용할 수 있는 방법 배움.
dictionary는 원소가 쌍인데, 어떻게 해야할지

```
fruit = ['apple', 'grape', 'orange', 'banana']
price = [3200, 15200, 9800, 5000]
_dict = dict(zip(fruit, price))

print(*_dict.keys()) # apple grape orange banana
print(*_dict.values()) # 3200 15200 9800 5000
print(*_dict.items()) # ('apple', 3200) ('grape', 15200) ('orange', 9800) ('banana', 5000)
```

다음과 같은 keys, values, items를 통해 내부 값을 unpacking할 수 있다.

---

## Reference

- Elice SW track 김병철 코치님, be pythonic.
  - 파이썬 언어 레퍼런스
  - 전문가를 위한 파이썬 (원제 Fluent Python) - 루시아누 하말류
  - Python Cookbook - 데이비드 비즐리, 브라이언 K. 존스
