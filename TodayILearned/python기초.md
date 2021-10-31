# 기초 python 문법

## 변수명 정하기

1. 영문과 숫자, \_로 이루어진다

2. 대소문자 구분한다

3. 문자나 \_로 시작한다

4. 특수문자를 사용하면 안된다.

5. 키워드를 사용하면 안된다. (if, for 등)

값 교환

a , b = b, a

## 출력 방식

```
print('number')
a, b, c = 1, 2, 3

print(a, b, c)
print("number : ", a,b,c)

print(a,b,c, sep = ', ')
print(a,b,c , sep = '')
print(a,b,c , sep = '\n')
print(a, end= ' ')
print(b, = end= ' ')
print(c)

```

```
a, b = map(int, input("숫자를 입력하세요 : ").split())
print(a+b)

```

## 조건문

```
x = 9
if x >= 10:
	if x%2 ==1:
	print("10이상의 홀수")

```

```
x = 9
if x >0 :
	if x < 10:
		print("10보다 작은 자연수")
```

```
x = 7
if x>0 and x <10 :
	print("10보다 작은 자연수") # 1~ 9까지 참

```

```
x = 7
if 0 < x <10 :
	print("10보다 작은 자연수") # 1~ 9까지 참

```

## 분기 조건문

```
x = 10
if x> 0 :
	print("양수")
else:
	print("음수")

```

## 다중 if문

```
x = 93
if x >=0 :
	print('A')
elif x >= 80 :
		print('B')
elif x >= 70:
		print('C')
elif x >= 60 :
		print('D')
else:
		print('F')
```

## 반복문(for, while,break, continue)

```
a = range(10)
print(list(a))
#[0,1,2,3,4,5,6,7,8,9]

```

```
a = range(1, 11)
print(list(a))
# [1,2,3,4,5,6,7,8,9,10]
```

```
for i in range(10, 0):
	print(i) #아무일도 안일어난다

```

```
for i in range(10, 0, -1):
	print(i) #10 9 8 7 6 5 4 3 2 1

```

```
for i in range(10, 0, -2):
	print(i) #10 8 6 4 2
```

## while 반복문

```
i = 1
while i <= 10 :
	print(i)
	i = i+1

```

```
i = 10
while i >= 1:
	print(i)
	i = i -1 #10~9 8 7 6 5 4 3 2 1
```

## break, continue

break : while 무한 반복 멈추게 한다. 특정조건에서 멈추게 한다던지!

```
i = 1
while True:
	print(i)
	if i == 10: # 10이되면 멈추어라
			break
	i += 1


```

```
i = 1
while <= 10 : or while True:
	print(i)
	if i == 5: # 5되면 멈추어라
			break
	i += 1
```

continue : for문으로 해보자 - 참이면 아래꺼 그냥 지나가버린다

```
for i in range(1, 11) :
		if i% 2 == 0:
			continue #( if문이 참이면 이 아래에 for문안에 있는 것들은 그냥 패스해줌)
		print(i) #홀수만 출력해주는 것!
```

for-else구문도 알아두어야한다.

```
for i in range(1, 11) :
		print(i)
		if i == 5:
			break #정상적이지않게 break되어서 끝내버리면 else하지못함
else :
	print(11)

# 1 2 3 4 5
```

```
for i in range(1, 11) :
		print(i)
		if i > 15:
			break #정상적이게 종료했다면
else :
	print(11) # 그아래도 출력

# 1 2 3 4 5 6 7 8 9 10 11
```

## 반복문을 이용한 문제풀이

1. 1부터 n까지 홀수 출력

2. 1부터 n까지의 합 구하기

3. n의 약수 출력하기

```
n = int(input())   # input은 str이므로 int로 묶어주어야 한다

for i in range(1, n+1) :
	if i % 2 == 1:
		print(i)
```

```
n = int(input())
sum = 0
for i in range(1, n+1) :
	sum = sum+ i
print(sum)
```

```
n = int(input())

for i in range( 1, n+1)"
	if n%i == 0:
		print(i, end = ' ')
```

## 중첩반복문 2중 for문

```
for i in range(5):
	for j in range(5):
		print(j, end = ' ')
	print()



```

```
for i in range(5):
	print('i:' i, sep='', end=' ')
	for j in range(5):
		print('j:', j, sep= '', end=' ')
	print()
```

```
for i in range(5):
	for j in range(5):
		print("*", end = ' ')
	print()

# * * * * *
# * * * * *
# * * * * *
# * * * * *
# * * * * *
```

```
for i in range(5):
	for j in range(i+1):
		print("*", end = ' ')
	print() #j포문끝나면 줄바꿈
# *
# * *
# * * *
# * * * *
# * * * * *
```

```
for i in range(5)
	for j in range(5-i):
		print("*", end = ' ')
	print() #j포문끝나면 줄바꿈
```

## 문자열과 내장함수

```
msg = 'It is Time"
print(msg.upper()) # 원본은 그대로, 출력값만 대문자로 보여줌
print(msg.lower())

tmp = msg.upper()
print(tmp)

print(tmp.find('T')) #T를 찾아서 index번호 반환

print(tmp.count('T'))#문자열몇개인지

#slice
msg[:2] #msg의 index 0 1까지 ( 2전까지) 보여줌
```

## 문자열 접근

```
len(msg) # 공백도 모두 센다. 총 10

for i in range(len(msg)):
	print(msg[i], end='')

```

```
#대문자만 출력

for x in msg:
	if x.isupper():
		print(x, end=' ')
print()

```

```
#소문자만 출력

for x in msg:
	if x.islower():
		print(x, end=' ')
print()

```

```
#공백 제거하고 출력 -알파벳일때만 참!

for x in msg:
	if x.isalpha():
		print(x, end='')
print()

```

## ord (문자 → 아스키넘버로)

```
#아스키 A~Z 까지 (65 ~90)
tmp = 'AZ'

for x in tmp:
	print(ord(x)) #ORD가 아스키넘버를 출력해주는 것!

```

```
#아스키 a-z까지 (97- 122)
tmp = 'az'

for x in tmp:
	print(ord(x)) #ORD가 아스키넘버를 출력해주는 것!
```

## chr 아스키 넘버 → 대응되는 문자로

```
tmp = 65
print(chr(tmp))
```

## 리스트와 내장함수

```

b = list()
print(b)

a = [1, 2, 3, 4, 5]
print(a)
print(a[0])

b = list(range(1, 11))
print(b)

c = a + b
print(c)
```

```
a = [1, 2, 3, 4, 5]
a.append(6)
# print(a) # [1, 2, 3, 4,5, 6]

a.insert(3, 7) # 3번 index에 7이 들어가는 것
#[ 1, 2, 3, 7, 4, 5, 6]
a.pop() # 맨 뒷자리 6 하나 없애주는 것

print(a)

a.pop(3) #3번인덱스값 꺼낸다는 뜻!
[1, 2, 3, 4, 5]
```

```
a.remove(4)
print(a)

```

```
print(a.index(5))

a = list(range(1, 11))
print(a)
#a리스트 전체 합 출력
print(sum(a))
#a라는 리스트에서 가장 큰 값 출력
print(max(a))
# a리스트 에서 가장 작은 값 출력
print(min(a))

# 최소값
min(7, 5)
#5
```

```
import random as r

r.shuffle(a) #a리스트 값 무조건 섞어라!!

a.sort() # 다시 원래대로 오름차순으로 정렬
```

```
a.sort(reverse = True) #내림차순 정렬!
```

```
a.clear()
#list에 있는 값들이 다 없어져버림!

```

## 리스트와 내장함수 2

```
a = [23, 12, 36, 53, 19]

print(a[:3])  # 처음부터 index3전까지!
print(a[1:4]) # 인덱스 1 2 3 까지!

```

```
# 요게 아래보다 좀 괜찮
for x in a :
	print(x, end = ' ')
print(x)

```

```
for i in range(len(a)):
	print(a[i], end = ' ')
print()

```

```
# 홀수 출력
for x in a :
	if x%2 == 1:
		print(x, end = ' ')
print()

```

```
for x in enumerate(a):
	print(x)

# enumerate 함수!  인덱스번호와 원소값을 주면서 x에 넘겨준다.
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d8659a6-4389-4d2e-8b8e-fc9c866f9f1a/Untitled.png)

(0, 23) (1, 12) (2, 36) 대입 INDEX번호와 값! 튜플형태로~

## 튜플

```
b = (1, 2, 3, 4, 5)
print(b[0])
b[0] = 7  # 에러 - 튜플이라 값 변경 불가능!
# 리스트는 변경 가능이지만
```

```
for x in enumerate(a):
	print(x[0], x[1])
print()

for index, value in enumerate(a):
	print(index, value)
print()
```

```
if all(60>x for x in a) :
	print("YES") #모두 다 참이어야 yes
else:
	print("NO")

```

```
if any(15>x for x in a) :
	print("YES") # 5개중에 하나만 참이어도
else:
	print("NO") #모두다 거짓이어야 nO!

```

## 2차원 리스트 생성과 접근

```
a = [0]*3
print(a)

```

크기 3인 1차원 리스트 생성됨!

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/85f0157c-3285-46c1-b378-824aabe83933/Untitled.png)

```
a = [[0] * 3 for _ in range(3) ]
print(a)
```

아래로는 행, 가로로는 열~

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b798052b-36b7-43c4-9a15-d8b3ea747f99/Untitled.png)

```
a = [[0] * 3 for _ in range(3) ]
#값 변경하기
a[0][1] = 1
print(a)
a[1][1] = 2
print(a)

```

```
for x in a :
	for y in x :
	print(y, end = ' ')

```

## 함수 만들기!

```
#define ! def

```

## 람다함수

```
def plus_one(x):
	return x+1

a = [1, 2, 3]

print(list(map(plus_one, a)))
#a자료구조가 plus_one함수영향받는 것!

```

```
print(list(map(lambda x : x+1, a)
```
