# 제어문

지금까지의 코드는 위에서부터 아래로 순차적으로 명령을 수행하는 프로그램을 작성하였습니다. 

제어문(Control of Flow)은 크게 반복문과 조건문으로 나눌 수 있고, 이는 순서도(Flow chart)로 표현이 가능합니다.


<center> 
    <img src="https://user-images.githubusercontent.com/18046097/61180553-25e87b00-a653-11e9-9895-7976d7204734.png", alt='if flowchart'/>
</center>


```python
# 위의 flow chart를 조건문을 통해 만들어봅시다.
```


```python
#
a = 5
if a > 5:
    print('5 초과')
else:
    print('5 이하')
```

    5 이하
    

## 조건문

1. `if` 문은 반드시 일정한 참/거짓을 판단할 수 있는 `조건식`과 함께 사용이 되어야한다.
`if <조건식>:`

1-1. `<조건식>`이 참인 경우 `:` 이후의 문장을 수행한다.

1-2. `<조건식>`이 거짓인 경우 `else:` 이후의 문장을 수행한다.

1-3. 여러 개의 `elif` 부가 있을 수 있고(없거나), **`else`는 선택적**이다.

* 이때 반드시 **들여쓰기를** 유의해야한다. 
파이썬에서는 코드 블록을 자바나 C언어의 `{}`와 달리 `들여쓰기`로 판단하기 때문이다.
* 앞으로 우리는 `PEP-8`에서 권장하는 `4spaces`를 사용할 것이다.


<center>
    <img src="https://user-images.githubusercontent.com/18046097/61180564-3a2c7800-a653-11e9-9fba-d60d2688ed3a.png", alt="if style"/>
</center>

<center><strong style="font-size: 30px;">우리는 4spaces를 맞춰서 씁니다!</strong></center>
<br>

<center>
    <img src="https://user-images.githubusercontent.com/18046097/61180566-3ac50e80-a653-11e9-81a6-2f195eeb0a65.png", alt="[space vs tab]"/>
</center>    




[출처 : 400,000 GitHub repositories, 1 billion files, 14 terabytes of code: Spaces or Tabs?](https://medium.com/@hoffa/400-000-github-repositories-1-billion-files-14-terabytes-of-code-spaces-or-tabs-7cfe0b5dd7fd)


### 조건문 연습
> 조건문을 통해 사용자가 입력한 날짜가 크리스마스인지 확인하세요.

---

```
예시 출력)
12/25
크리스마스입니다.
```



```python
is_christmas = input('날짜를 입력해주세요 ex)12/24 : ')

# 아래에 코드를 작성하세요
```


```python
#
if is_christmas == '12/25':
    print('크리스마스입니다.')
else:
    print('크리스마스가 아닙니다.')
```

### 조건문 활용


> 조건문을 통해 변수 num의 값과 홀수/짝수 여부를 출력하세요.

---

```
예시 출력)
3
홀수입니다.
```


```python
num = int(input('숫자를 입력하세요 : '))

# 아래에 코드를 작성하세요
```


```python
#
if num % 2 == 1: # num % 2: 나머지가 있으면
    print('홀수입니다.')
else:
    print('짝수입니다.')
```

## 복수 조건문

**2개 이상의 조건문**을 활용할 경우 `elif <조건식>:`을 활용합니다.
<center>
<img src="https://user-images.githubusercontent.com/18046097/61180560-3993e180-a653-11e9-8263-79bd7bc6eed7.png", alt="elif">
</center>

### 복수조건문 활용

> 조건문을 통해 변수 score에 따른 평점을 출력하세요.

|점수|등급|
|---|---|
|90점 이상|A|
|80점 이상|B|
|70점 이상|C|
|60점 이상|D|
|60점 미만|F|

--- 

```
예시 출력)
B
```


```python
score = int(input('점수를 입력하세요 : '))

# 아래에 코드를 작성하세요
```


```python
#
if score >= 90:
    print('A')
elif score>= 80:
    print('B')
elif score>= 70:
    print('C')
elif score>= 60:
    print('D')
else:
    print('F')
```

### 중첩조건문 활용

> 위 실습문제 2개 코드를 활용하여 
95점 이상이면, 등급과 함께 "참 잘했어요"도 함께 출력해주세요.

--- 

```
예시 출력)
A
참잘했어요.
```


```python
score = 96

# 아래에 코드를 작성하세요
```


```python
#
if score >= 95:
    print('A\n' '참 잘했어요.')
elif score >= 90:
    print('A')
elif score >= 80:
    print('B')
elif score >= 70:
    print('C')
elif score >= 60:
    print('D')
else:
    print('F')
```


```python
if score >= 90:
    print('A')
    if score >= 95:
         print('참 잘했어요.')
elif score >= 80:
    print('B')
elif score >= 70:
    print('C')
elif score >= 60:
    print('D')
else:
    print('F')
```

## 조건 표현식(Conditional Expression)

표현식은 보통 조건에 따라 값을 정할 때 많이 활용됩니다.

---

**활용법**

```python
true_value if <조건식> else false_value
조건문이 참인 경우 if <조건식> else 조건문이 거짓인 경우
```


```python
num = int(input('숫자를 입력하세요 : '))

print('0 보다 큼') if num > 0 else print('0 보다 크지않음')
```


```python
# 아래의 코드는 무엇을 위한 코드일까요?
num = int(input('숫자를 입력하세요 : '))
value = num if num >= 0 else 0
print(value)

# 아래에 답변을 작성하세요.
```


```python
#
# 0 혹은 양의 정수이면 그대로 출력, 음의 정수이면 0을 출력
```

### 조건표현식과 동일한 `if`문 작성하기

> 다음의 코드와 동일한 `if`문을 작성해보세요.

```python
num = -5
value = num if num >= 0 else 0
print(value)
```
---

```
예시 출력)
0
```


```python
# 아래에 코드를 작성하세요.
```


```python
#
num = -5
if num >= 0:
    value = num
else:
    value = 0
    
print(value)
```

### 조건표현식 만들어보기

> 다음의 코드와 동일한 조건 표현식을 작성해보세요.

```python
num = 2
if num % 2:
    result = '홀수입니다.'
else:
    result = '짝수입니다.'
print(result)
```
---
```
예시 출력)
짝수입니다.
```


```python
# 아래에 코드를 작성하세요.
```


```python
#
num = int(input('숫자를 입력해주세욤: '))
print('홀수입니다.') if num % 2 else print('짝수입니다.')
```

# 반복문

## `while` 문

`while` 문은 조건식이 참(True)인 경우 반복적으로 코드를 실행합니다.

**그래서 종료조건을 반드시 설정해주어야 합니다.**

<br>
<br>
<center> 
    <img src="https://user-images.githubusercontent.com/18046097/61180568-3ac50e80-a653-11e9-9960-ba15137290a6.png", alt="while"/>
</center>


```python
# 위의 flow chart를 조건문을 통해 만들어봅시다.
# 아래에 코드를 작성하세요.
```


```python
#
a = 0
while a < 5:
    print(a)
    a += 1
    
```

<center>
    <img src="https://user-images.githubusercontent.com/18046097/61180567-3ac50e80-a653-11e9-9f12-39c404f4be30.png", alt="">
</center>

`while` 문 역시 `<조건식>` 이후에 `:`이 반드시 필요하며, 

이후 오는 코드 블록은 `4spaces`로 **들여쓰기**를 해주셔야 합니다.

### `while`문 작성하기
> 사용자가 "안녕"이라고 입력할 때까지 인사하는 코드를 작성해보세요.


```python
# 아래에 코드를 작성하세요.
```


```python
hello = ''
while hello != '안녕':
    print('안녕이라고 말해!!!!!!!!!!!!')
    hello = input('당장 말해!!!!!')
```

## `for` 문

`for` 문은 정해진 범위 내 시퀀스(문자열, 튜플, 리스트 같은)나 다른 반복가능한 객체(iterable)의 요소들을 순차적으로 코드를 실행합니다.

---

**활용법**

```python
for element in iterable:
    code line1
    code line2
```

<center>
    <img src="https://user-images.githubusercontent.com/18046097/61180565-3a2c7800-a653-11e9-806a-28838248de31.png", alt="">
</center>


```python
# flowchart를 for문을 통해 코드로 작성해봅시다.
# 아래에 코드를 작성하세요.
```


```python
#
for a in range(5):
    print(a)
print('끝')
```

    0
    1
    2
    3
    4
    끝
    

![for animation](https://user-images.githubusercontent.com/18046097/61180563-3a2c7800-a653-11e9-8a7a-c7d6e6b30141.gif)

for 문에서 요소 값에 다른 값을 할당해도 다음 반복구문에 영향을 주지 않습니다.

다음 range 요소 값에 의해 덮어 씌워지기 때문입니다.


```python
#
for i in range(10):
    print(i)
    i = '안녕'
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    

### `for` 문 연습
> for 문을 활용하여 사용자가 입력한 문자를 한글자씩 출력해보세요.

---

```
예시 출력)
문자를 입력하세요 : 안녕!
안
녕
!
```



```python
chars = input('문자를 입력하세요 : ')

# 아래에 코드를 작성하세요.
```

    문자를 입력하세요 : 안녕!
    


```python
#
for char in chars:
    print(char)
```

    안
    녕
    !
    

###  `for` 문과 `if` 문 작성하기

> 반복문과 조건문만 활용하여 1~30까지 숫자 중에 홀수만 담긴 리스트를 만드세요.
- list에서 값 추가는 `.append()`로 합니다.

---
```
예시 출력)
[1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
```


```python
# 아래에 코드를 작성하세요.
```


```python
#
result = []
for i in range(1, 31):
    if i % 2:
        result.append(i)

print(result)
```

    [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
    

### index와 함께 `for` 문 활용

> `enumerate()`를 활용하면, 추가적인 변수를 활용할 수 있습니다.
- `enumerate()`는 [파이썬 표준 라이브러리의 내장함수](https://docs.python.org/ko/3.6/library/functions.html) 중 하나이며, 다음과 같이 구성되어 있다.
>
> <center>
    <img src="https://user-images.githubusercontent.com/18046097/61180561-3993e180-a653-11e9-9558-085c9a0ad65d.png", alt="enumerate">
</center>


```python
# enumerate()를 활용해서 출력해봅시다.
lunch = ['짜장면', '초밥']
```


```python
# enumerate - 인덱스, value 값 순서로

for idx, menu in enumerate(lunch):
    print(idx, menu)
```

    0 짜장면
    1 초밥
    


```python
# enumerate()를 사용하였을 때 어떻게 표현이 되는지 확인해봅시다.
```


```python
#
classroom = ['kim', 'lee', 'park', 'choi']
class_list = list(enumerate(classroom))
print(class_list)
```

    [(0, 'kim'), (1, 'lee'), (2, 'park'), (3, 'choi')]
    


```python
# 숫자를 1부터 카운트 할 수도 있습니다. 
```


```python
#
for idx, menu in enumerate(lunch, start=3):
    print(idx, menu)
```

    3 짜장면
    4 초밥
    


```python
#
```

### dictionary 반복문 활용

기본적으로 dictionary를 `for` 문을 시행시키면 다음과 같이 시행됩니다.


```python
# 옆자리 친구의 이름을 활용하여 dictionary를 만들어봅시다.
```


```python
#
classroom = {
    'teacher': 'justin',
    'student1': 'saejin',
    'student2': 'luke'
}

for member in classroom:
    print(member)
```

    teacher
    student1
    student2
    

dictionary의 **`key`를 출력함으로써 `value`에도 접근**할 수 있기 때문입니다.

따라서 dictionary의 value를 출력하기 위해서는 아래와 같이 작성합니다.


```python
# value를 출력해봅시다.
```


```python
#
for member in classroom:
    print(f'이것은 사전의 키: {member}')
    print(f'이것은 사전의 키를 통해 추출한 value: {classroom[member]}')
```

    이것은 사전의 키: teacher
    이것은 사전의 키를 통해 추출한 value: justin
    이것은 사전의 키: student1
    이것은 사전의 키를 통해 추출한 value: saejin
    이것은 사전의 키: student2
    이것은 사전의 키를 통해 추출한 value: luke
    

* dictionary에서 `for` 활용하는 4가지 방법

```python
# 0. dictionary (key 반복)
for key in dict:
    print(key)


# 1. key 반복
for key in dict.keys():
    print(key)
    
    
# 2. value 반복    
for val in dict.values():
    print(val)

    
# 3. key와 value 반복
for key, val in dict.items():
    print(key, val)

```


```python
# 하나씩 써봅시다.
phone_book = {'서울': '02', '부산': '051', '대구': '053', '경북': '054'}
```


```python
#1. 단순 dictionary 반복
for city in phone_book:
    print(city)
```

    서울
    부산
    대구
    경북
    


```python
#2. key 반복
for city in phone_book.keys():
    print(city)
```

    서울
    부산
    대구
    경북
    


```python
#3. value 반복
for number in phone_book.values():
    print(number)
```

    02
    051
    053
    054
    


```python
#4. key-value 반복
for location, number in phone_book.items():
    print(location, number)
    print(f'{location}의 지역 번호는 {number}입니다.')
```

    서울 02
    서울의 지역 번호는 02입니다.
    부산 051
    부산의 지역 번호는 051입니다.
    대구 053
    대구의 지역 번호는 053입니다.
    경북 054
    경북의 지역 번호는 054입니다.
    

### dictionary `for`문 작성하기

> 4가지 반복문을 활용해보고 출력되는 결과를 확인해보세요.

```
blood_type = {'A': 4, 'B': 2, 'AB': 3, 'O':1}
```

---

```
예시 출력)
혈액형의 종류는 다음과 같습니다 =>  A B AB O
혈액형의 종류는 다음과 같습니다 =>  A B AB O
총인원은 10명입니다.
A형은 4명입니다. ... O형은 1명입니다.
```


```python
blood_type = {'A': 4, 'B': 2, 'AB': 3, 'O': 1}

# 아래에 코드를 작성하세요.
```


```python
#1. 혈액형의 종류는 다음과 같습니다 => A B AB O  가 출력되게 해주세요(단순 반복 활용)
my_str = '혈액형의 종류는 다음과 같습니다 => '
for type in blood_type:
    my_str += type + ' '
    
print(my_str)
```

    혈액형의 종류는 다음과 같습니다 => A B AB O 
    


```python
#2. 혈액형의 종류는 다음과 같습니다 => A B AB O  가 출력되게 해주세요 (.keys 활용)
my_str = '혈액형의 종류는 다음과 같습니다 => '
for type in blood_type.keys():
    my_str += type + ' '
    
print(my_str)
```

    혈액형의 종류는 다음과 같습니다 => A B AB O 
    


```python
#3. 총인원은 10명입니다.  가 출력되게 해주세요 
result = 0
for people in blood_type.values():
    result += people
    
print(f'총인원은 {result}명입니다.')
```

    총인원은 10명입니다.
    


```python
"""
A형은 4명입니다.
B형은 2명입니다.
AB형은 3명입니다.
O형은 1명입니다.
""" 

#4. 위와 같은 결과가 출력되게 해주세요
for blood, num in blood_type.items():
    print(f'{blood}형은 {num}명입니다.')

```

    A형은 4명입니다.
    B형은 2명입니다.
    AB형은 3명입니다.
    O형은 1명입니다.
    

### dictionary 값 추가 
- 딕셔너리에 값 추가 
- 자료구조 파트에서 더 자세하게 함


```python
# 
my_dict = {}
my_dict['apple'] = 1
my_dict['watermelon'] = 2
print(my_dict)
```

    {'apple': 1, 'watermelon': 2}
    

### dictionary 구축하기 (`for`, `if`)

> `in` 연산자와 `if` 문을 활용하면 dictionary에서 특정 key가 존재하는지 여부를 알아낼 수 있습니다.


```python
# 
dusts = {
    '서울': 78,
    '대전': 60,
    '구미': 40,
    '광주': 50
}

print('구미' in dusts)
print('부산' in dusts)
```

    True
    False
    

### dictionary 구축하기 (`for`, `if`)
> 다음과 같은 리스트가 있을 때 각각의 요소의 개수를 value 값으로 갖는 딕셔너리를 만드세요.
> ```python
book_title =  ['great', 'expectations', 'the', 'adventures', 'of', 'sherlock', 'holmes', 'the', 'great', 'gasby', 'hamlet', 'adventures', 'of', 'huckleberry', 'fin']
```

---



```
예시 출력)
{'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}
```



```python
book_title =  ['great', 'expectations', 'the', 'adventures', 'of', 'sherlock', 'holmes', 'the', 'great', 'gasby', 'hamlet', 'adventures', 'of', 'huckleberry', 'fin']

# 아래에 코드를 작성하세요.
```


```python
#
# 1. for, if 활용
title_counter = {}
for title in book_title:
    if title not in title_counter:
        title_counter[title] = 1
    else:
        title_counter[title] += 1

print(title_counter)
```

    {'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}
    


```python
##
# 2 .count() 활용
title_counter = {}
for title in book_title:
    title_counter[title] = book_title.count(title)
    
print(title_counter)
```

    {'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}
    


```python
##
# 3 .get() method 활용(4장에서 다시 배웁니다.)

title_counter = {}
for title in book_title:
    title_counter[title] = title_counter.get(title, 0) + 1
    
print(title_counter)
```

    {'great': 2, 'expectations': 1, 'the': 2, 'adventures': 2, 'of': 2, 'sherlock': 1, 'holmes': 1, 'gasby': 1, 'hamlet': 1, 'huckleberry': 1, 'fin': 1}
    

> `get(key[, default])`
* key 가 딕셔너리에 있는 경우 key 에 대응하는 값을 돌려주고, 그렇지 않으면 default 를 돌려준다. 


```python
# .get은 이렇게 활용할 수 있습니다.
a = {'a': 1, 'b': 2, 'c': 3}
```


```python
# 
print(a['d'])
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-75-1e4204d09bcf> in <module>
          1 #
    ----> 2 print(a['d'])
    

    KeyError: 'd'



```python
# 
print(a.get('d'))
print(a.get('d', 4))
print(a)
```

    None
    4
    {'a': 1, 'b': 2, 'c': 3}
    

## `range()` 함수
- 숫자들의 시퀀스로 반복 할 필요가 있으면 사용하는 함수입니다. 수열을 만듭니다.


`range(start, stop[, step])`
- step 인자가 생략되면 기본값 `1`이 사용된다. 
- start 인자가 생략되면 기본값 `0`이 사용된다. 
- step 이 `0`이면 `ValueError`를 일으킨다.


**장점**
- list 나 tuple 에 비해 범위의 크기에 무관하게 항상 같은 (작은) 양의 메모리를 사용한다. (start, stop, step 값만을 저장).

**주의사항**
- range() 가 돌려준 객체(iterable)는 리스트인 것 같지만, 리스트가 아니다. 
- 반복(이터레이트)할 때 원하는 시퀀스 항목들을 순서대로 돌려주는 객체이지만, 실제로 리스트를 만들지 않아서 공간을 절약하는 것이다.
- 만약 리스트로 만들고자 한다면 `list()` 함수를 사용한다.


```python
#
print(range(10))
```

    range(0, 10)
    


```python
# 리스트 함수를 사용해 range() 객체를 리스트로 만들어 봅시다.
list(range(10))
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
# range 함수로 0~9 범위를 반복하는 for 문을 작성해봅시다.
for i in range(10):
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    

## `break`, `continue`, `else`, `pass`

### `break`

`break` 문은 **반복문을 종료**하는 표현입니다. 

`for` 나 `while` 문으로부터 빠져나가게 만듭니다.


```python
# break 문을 활용해봅시다.
```


```python
#
for i in range(10):
    if i > 1:
        print('0과 1만 필요해~!~!')
        break
    print(i)
```

    0
    1
    0과 1만 필요해~!~!
    

### `break` 작성하기

> 조건문과 반복문, `break`를 활용하여 리스트에서 쌀이 나왔을때 `for` 문을 멈추는 코드를 작성하세요.

```python
rice = ['보리', '보리', '보리', '쌀', '보리']
```

---

```
예시 출력)
보리
보리
보리
쌀
잡았다!
```


```python
rice = ['보리', '보리', '보리', '쌀', '보리']

# 아래에 코드를 작성하세요.
```


```python
#
for str in rice:
    if str == '쌀':
        print('쌀!!!\n요놈 잡았다!!')
        break
    print(str)
```

    보리
    보리
    보리
    쌀!!!
    요놈 잡았다!!
    

> 조건문과 반복문, break를 활용하여 다음 headlines 리스트의 요소들을 130자 크기의 하나의 문자열로 이어 붙이는 코드를 작성하세요.

```python
headlines = [
    "Local Bear Eaten by Man",
    "Legislature Announces New Laws",
    "Peasant Discovers Violence Inherent in System",
    "Cat Rescues Fireman Stuck in Tree",
    "Brave Knight Runs Away",
    "Papperbok Review: Totally Triffic"
]
```

---

```
예시 출력)
Local Bear Eaten by Man Legislature Announces New Laws Peasant Discovers Violence Inherent in System Cat Rescues Fireman Stuck in
```


```python
headlines = [
    'Local Bear Eaten by Man',
    'Legislature Announces New Laws',
    'Peasant Discovers Violence Inherent in System',
    'Cat Rescues Fireman Stuck in Tree',
    'Brave Knight Runs Away',
    'Papperbok Review: Totally Triffic',
]

# 아래에 코드를 작성하세요.
```


```python
#
sentence = ''

for str in headlines:
    sentence += str + ' '
    if len(sentence) >= 130:
        sentence = sentence[:130]
print(sentence)
```

    Local Bear Eaten by Man Legislature Announces New Laws Peasant Discovers Violence Inherent in System Cat Rescues Fireman Stuck in 
    

### `continue` 

`continue`문은 continue 이후의 코드를 수행하지 않고 다음 요소를 선택해 반복을 계속 수행합니다.


```python
# continue 문을 활용해봅시다.
```


```python
#

for i in range(6):
    if i % 2 == 0:
        continue
        print(f'{i}는 짝수다.')
    print(f'{i}는 홀수다.')
```

    1는 홀수다.
    3는 홀수다.
    5는 홀수다.
    

### `continue` 작성하기

> 나이가 입력된 리스트가 있을때,
> 조건문과 반복문, continue를 활용하여 20살 이상일때만 "성인입니다"라는 출력을 하는 코드를 작성하세요.

```python
ages = [10, 23, 8, 30, 25, 31]
```

---

```
예시 출력)
23 살은 성인입니다.
30 살은 성인입니다.
25 살은 성인입니다.
31 살은 성인입니다.
```


```python
ages = [10, 23, 8, 30, 25, 31, 20]

# 아래에 코드를 작성하세요.
```


```python
#
for i in ages:
    if i < 20:
        continue
    print(f'{i}살은 성인입니당~')
```

    23살은 성인입니당~
    30살은 성인입니당~
    25살은 성인입니당~
    31살은 성인입니당~
    20살은 성인입니당~
    

### `else`

- `else` 문은 **끝까지 반복문을 시행한 이후에 실행**된다.
- 반복에서 리스트의 소진이나 (`for` 의 경우) 조건이 거짓이 돼서 (`while` 의 경우) 종료할 때 실행된다. 
- 하지만 반복문이 **`break` 문으로 종료할 때는 실행되지 않는다.** (`break`를 통해 중간에 종료되지 않은 경우만 실행)


```python
# break가 안되는 상황을 만들어봅시다.
```


```python
#
for i in range(3):
    print(i)
    if i == 100:
        print(f'{1}에서 break 시행됨.')
        break

else:
    print('break 시행 안 됨.')
```

    0
    1
    2
    break 시행 안 됨.
    


```python
# break가 되는 상황을 만들어봅시다.
```


```python
#
for i in range(3):
    print(i)
    if i == 1:
        print(f'{1}에서 break 시행됨.')
        break
else:
    print('break 시행 안 됨.')
```

    0
    1
    1에서 break 시행됨.
    

### `else` 문 작성하기

> 조건문과 반복문, break, else 를 통해서 아래의 코드와 동일한 코드를 작성하세요.
* 3이 있을 경우 True를 print하고, 아닐 경우 모든 값과 함께 False를 print 한다.

```python
numbers = [1, 5, 10]
```

---

```
예시 출력)
False
```


```python
numbers = [1, 5, 10]

# 아래에 코드를 작성하세요.
```


```python
#
for i in numbers:
    if i == 3:
        print('True')
        break
else:
    print('False')
```

    False
    

### `pass`
pass 문은 아무것도 하지 않습니다. 
문법적으로 문장이 필요하지만, 프로그램이 특별히 할 일이 없을 때 자리를 채우는 용도로 사용할 수 있습니다.

**`pass` 와 `continue` 차이**


```python
# pass
for i in range(5):
    if i == 3:
        pass
    print(i)
```

    0
    1
    2
    3
    4
    


```python
# continue
for i in range(5):
    if i == 3:
        continue
    print(i)
```

    0
    1
    2
    4
    
