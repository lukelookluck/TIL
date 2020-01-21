# Python 기초

## 개요

본 강의 자료는 [Python 공식 Tutorial](https://docs.python.org/3.7/tutorial/index.html)에 근거하여 만들어졌으며, Python 3.7 버전에 해당하는 내용을 담고 있습니다.

또한, 파이썬에서 제공하는 스타일 가이드인 [`PEP-8`](https://www.python.org/dev/peps/pep-0008/) 내용을 반영하였습니다. 

파이썬을 활용하는 다양한 IT기업들은 대내외적으로 본인들의 스타일 가이드를 제공하고 있습니다. 

* [구글 스타일 가이드](https://github.com/google/styleguide/blob/gh-pages/pyguide.md)
* [Tensorflow 스타일 가이드](https://www.tensorflow.org/community/style_guide)

## 식별자

파이썬에서 식별자는 변수, 함수, 모듈, 클래스 등을 식별하는데 사용되는 이름(name)입니다. 

* 식별자의 이름은 영문알파벳(대문자와 소문자), 밑줄(_), 숫자로 구성된다.
* 첫 글자에 숫자가 올 수 없다.
* 길이에 제한이 없다.
* 대소문자(case)를 구별한다.
* 아래의 예약어는 사용할 수 없다. 

```
False, None, True, and, as, assert, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
```


```python
# 예약어들을 직접 확인해봅시다.
```


```python
# import 구문은 모듈파트에서 다시 알아봅시다.
import keyword
print(keyword.kwlist)
```

    ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
    

*  내장함수나 모듈 등의 이름으로도 만들면 안된다.


```python
# 내장함수의 이름을 사용하면 어떤일이 일어나는지 확인해봅시다.
```


```python
# str은 값을 문자로 바꿔주는 내장함수입니다.
str(5)
```




    '5'




```python
# 예시로 str에 값을 할당해보고, 오류를 확인해봅시다.
# str은 이제 'hi'라는 값으로 인식되기 때문에 이전의 기능을 수행하지 못합니다.
str = 'hi'
str(5)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-9-8a8229a49a52> in <module>
          2 # str은 이제 'hi'라는 값으로 인식되기 때문에 이전의 기능을 수행하지 못합니다.
          3 str = 'hi'
    ----> 4 str(5)
    

    TypeError: 'str' object is not callable



```python
# 뒤에서 진행될 코드에 영향이 갈 수 있기 때문에 방금 생성한 str을 삭제합니다.
del str
```

## 기초 문법

### 인코딩 선언

인코딩은 선언하지 않더라도 `UTF-8`로 기본 설정이 되어있습니다.

만약, 인코딩을 설정하려면 코드 상단에 아래와 같이 선언합니다.
주석으로 보이지만, Python `parser`에 의해 읽혀집니다.

```python
# -*- coding: <encoding-name> -*- 
```

### 주석(Comment)

* 주석은 `#`으로 표현한다. 


* `docstring`은 `"""`으로 표현한다. 
    * 여러 줄의 주석을 작성할 수 있으며, 보통 함수/클래스 선언 다음에 해당하는 설명을 위해 활용한다.
   
   
* 예시 : [flask 공식 문서](https://github.com/pallets/flask/blob/master/src/flask/app.py#L1281) 일부 발췌

![flask 공식문서 예시](https://user-images.githubusercontent.com/18046097/61179848-f3845100-a645-11e9-99df-bbe9c2246d7d.png)


```python
# 주석을 연습해봅시다. 
```


```python
# 이 줄은 실해되지 않습니다.
def mysum(a, b):
    """이 것은 덧셈 함수입니다.
    이 줄도 실행되지 않아요.
    다만, docstring인 이유가 있습니다.
    """
```


```python
# docstring은 다음과 같이 확인할 수 있습니다.
```


```python
#
mysum.__doc__
```




    '이 것은 덧셈 함수입니다.\n    이 줄도 실행되지 않아요.\n    다만, docstring인 이유가 있습니다.\n    '




```python
# 내장함수의 docstring도 확인해봅시다.
sum.__doc__
```




    "Return the sum of a 'start' value (default: 0) plus an iterable of numbers\n\nWhen the iterable is empty, return the start value.\nThis function is intended specifically for use with numeric values and may\nreject non-numeric types."



### 코드 라인
* 기본적으로 파이썬에서는 `;` 을 작성하지 않는다.

* 한 줄로 표기할 떄는 `;`를 작성하여 표기할 수 있다. 


```python
# print문을 두번 써보자.
```


```python
#
print('hello')
print('world')
```

    hello
    world
    


```python
# print문을 한줄로 이어서 써봅시다. 오류 메시지를 확인해주세요.
```


```python
#
print('hello')print('world')
```


      File "<ipython-input-19-a44e84f4a934>", line 2
        print('hello')print('world')
                          ^
    SyntaxError: invalid syntax
    



```python
# ;을 통해 오류를 해결해봅시다.
```


```python
#
print('hello');print('world')
```

    hello
    world
    

* 줄을 여러줄 작성할 때는 역슬래시`\`를 사용하여 아래와 같이 할 수 있다. 


```python
# print문을 통해 안되는 코드 예시 작성해봅시다.
```


```python
#end of line
print('
dd')
```


      File "<ipython-input-20-2517f3288de5>", line 2
        print('
               ^
    SyntaxError: EOL while scanning string literal
    



```python
# print문을 통해 되는 코드 예시 작성해봅시다.
```


```python
# 아래와 같은 동작이 가능 하지만 잘 쓰이지는 않습니다.
```


```python
#
print('\
dd')
```

    dd
    

* `[]` `{}` `()`는 `\` 없이도 가능하다.


```python
# list를 두 줄에 걸쳐서 만들어봅시다.
```


```python
#
lunch = [
    '짜장면', '짬뽕',
    '탕수육', '유린기',
]

lunch = [
    '짜장면', '짬뽕',
    '탕수육', '유린기',
]
```


```python
## pep8 가이드에 따르면 여러 줄의 생성자의 닫히는 괄호(소, 중, 대)는 
## 마지막 줄의 공백이 아닌 첫번째 문자(요소) 위치에 오거나 마지막 줄에서 생성자가 시작되는 첫번째 열에 위치합니다.
```

# 변수(variable) 및 자료형


<center><img src="https://user-images.githubusercontent.com/18046097/61179855-0c8d0200-a646-11e9-9e9e-2c6df0504296.png", alt="variable"/></center>


<center><img src="https://user-images.githubusercontent.com/18046097/61179857-13b41000-a646-11e9-9a88-8487df4eaf52.png", alt="box"/></center>

* 변수는 `=`을 통해 할당(assignment) 된다. 

* 해당 자료형을 확인하기 위해서는 `type()`을 활용한다.

* 해당 변수의 메모리 주소를 확인하기 위해서는 `id()`를 활용한다.


```python
# 변수에 값을 할당해봅시다.
```


```python
#
x = 'ssafy'
```


```python
# type()을 사용해봅시다.
```


```python
#
type(x)
```




    str




```python
# id()를 사용해봅시다.
```


```python
#
id(x)
```




    3115231305656




```python
# 같은 값을 동시에 할당해봅시다.
```


```python
#
x = y = 1993
print(x, y)
```

    1993 1993
    

* 다른 값을 동시에 할당 가능하다.


```python
# 동시에 두개의 변수에 값 두개를 할당해봅시다.
```


```python
#
x,y = 1, 2
print(x, y)
```

    1 2
    


```python
# 패킹(packinbg)/언패킹(unpacking)
# 패킹 
tuple_sample = 1, 2, 3
print(tuple_sample)

# 언패킹
a, b, c = tuple_sample
print(a, b, c)
```

    (1, 2, 3)
    1 2 3
    


```python
# 변수의 개수가 더 많을 때 오류를 알아봅시다.
```


```python
#
x, y = 1
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-34-3870f60602db> in <module>
          1 #
    ----> 2 x, y = 1
    

    TypeError: cannot unpack non-iterable int object



```python
# 변수의 개수가 더 적을 때 오류를 알아봅시다.
```


```python
#
x, y = 1, 2, 3, 4
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-35-0cd1e6f8aded> in <module>
          1 #
    ----> 2 x, y = 1, 2, 3, 4
    

    ValueError: too many values to unpack (expected 2)


* 이를 활용하면 서로 값을 바꾸고 싶은 경우 아래와 같이 활용 가능하다.


```python
# 변수 x와 y의 값을 바꿔봅시다.
```


```python
#
x, y = y, x
print(x, y)
```

    2 1
    


```python
# 다른 언어에서 변수 값을 바꾸면?
x = 1
y = 2

c = x

x = y
y = c
print(x, y)
```

    2 1
    

## 숫자 형(Numbers)
[python doc 숫자 형](https://docs.python.org/ko/3.7/library/stdtypes.html#numeric-types-int-float-complex)

###  `int` (정수, ingtegers)

모든 정수는 `int`로 표현됩니다.

파이썬 3.x 버전에서는 `long` 타입은 없고 모두 `int` 타입으로 표기 됩니다.

* python 3.x에서 long은 없어졌다.
* 보통 프로그래밍 언어 및 파이썬 2.x에서의 long은 OS 기준 32/64비트이다.
* 파이썬 3.x에서는 모두 int로 통합되었다.

8진수 : `0o` / 2진수 : `0b` / 16진수: `0x` 로도 표현 가능합니다. 


```python
# 변수에 정수를 넣고 해당 변수의 type을 알아봅시다.
```


```python
#
a = 3
type(a)
```




    int




```python
#
a = 2**64
print(a)
type(a)
```

    18446744073709551616
    




    int



**파이썬에서 표현할 수 있는 가장 큰 수**
* 파이썬에서 가장 큰 숫자를 활용하기 위해 sys 모듈을 불러온다.
* 파이썬은 기존 C 계열 프로그래밍 언어와 다르게 정수 자료형(integer)에서 오버플로우가 없다.
* arbitrary-precision arithmetic를 사용하기 때문이다. 

> **오버플로우(overflow)**
- 데이터 타입 별로 사용할 수 있는 메모리의 크기가 제한되어 있다.
- 표현할 수 있는 수의 범위를 넘어가는 연산을 하게 되면, 기대했던 값이 출력되지 않는 현상, 즉 메모리가 차고 넘쳐 흐르는 현상

> **arbitrary-precision arithmetic**
- [파이썬에서 아주 큰 정술을 표현할 때 사용하는 메모리의 크기 변화](https://mortada.net/can-integer-operations-overflow-in-python.html)
- 사용할 수 있는 메모리양이 정해져 있는 기존의 방식과 달리, 현재 남아있는 만큼의 가용 메모리를 모두 수 표현에 끌어다 쓸 수 있는 형태
- 특정 값을 나타내는데 4바이트가 부족하다면 5바이트, 더 부족하면 6바이트까지 사용할 수 있게 유동적으로 운용



```python
#
import sys
max_int = sys.maxsize
#sys.maxsize의 값은 2**63-1 => 64비트에서 부호 비트를 제외한 63개의 최대치
print(max_int)

super_max = sys.maxsize * sys.maxsize
print(super_max)
```

    9223372036854775807
    85070591730234615847396907784232501249
    


```python
# n진수를 만들어보고, 출력해봅시다.
```


```python
#
binary_number = 0b10 # 2
octal_number = 0o10 # 8
decimal_number = 10 #10
hexadecimal_number = 0x10 # 16


print(f"""
2진수 : {binary_number}
8진수 : {octal_number}
10진수 : {decimal_number}
16진수 : {hexadecimal_number}
""")
```

    
    2진수 : 2
    8진수 : 8
    10진수 : 10
    16진수 : 16
    
    

### `float`(부동소수점, 실수, floating point numbers)

실수는 `float`로 표현됩니다. 

다만, 실수를 컴퓨터가 표현하는 과정에서 부동소수점을 사용하며, 항상 같은 값으로 일치되지 않습니다. (floating point rounding error)

이는 컴퓨터가 2진수(비트)를 통해 숫자를 표현하는 과정에서 생기는 오류이며, 대부분의 경우는 중요하지 않으나 값을 같은지 비교하는 과정에서 문제가 발생할 수 있습니다.


```python
# 변수에 실수를 넣고 해당 변수의 type을 알아봅시다.
```


```python
#
a = 3.5
type(a)
```




    float



**컴퓨터식 지수 표현 방식**
* e를 사용할 수도 있다. (e와 E 둘 중 어느 것을 사용해도 무방)


```python
#
b = 314e-2 # 314*0.01
print(type(b))
print(b)
```

    <class 'float'>
    3.14
    


```python
number = 314159E-4
print(number)
```

    31.4159
    

**실수의 연산**
* 실수의 경우 실제로 값을 처리하기 위해서는 조심할 필요가 있다.


```python
# 실수의 덧셈을 해봅시다.
```


```python
#
3.5 + 3.2 
```




    6.7




```python
# 실수의 뺄셈을 해봅시다.
```


```python
# 2진수의 부동소수점으로 계산하기 때문에 값이 저렇게 나옴
3.5 - 3.1207
```




    0.3793000000000002




```python
# 우리가 원하는대로 반올림을 해봅시다.
# round() 는 0~4는 내림, 5는 동일하게 작동하지 않고 반올림 방식에 따라 다릅니다.
# 짝수에서 5는 내림 / 홀수에서 5는 올림
```


```python
# 2번째 자리까지 표시
round(3.5 - 3.12, 2)
```




    0.38




```python
# 두 개의 값이 같은지 확인해봅시다.
```


```python
#
3.5 - 3.12 == 0.38
```




    False




```python
#
round(3.5 - 3.12, 2) == 0.38
```




    True



* 따라서 다음과 같은 방법으로 실수 비교 연산을 처리 할 수 있다. (이외에 다양한 방법이 있음)


```python
# 1. 기본적인 처리방법을 알아봅시다.
# 1e-10 : 1 *0.00~01
```


```python
#
a = 3.5 - 3.12
b = 0.38

abs(a - b) <= 1e-10
```




    True




```python
# 2. sys 모듈을 통해 처리하는 방법을 알아봅시다.
# `epsilon` 은 부동소수점 연산에서 반올림을 함으로써 발생하는 오차 상환
# 어떤 실수를 가장 가까운 부동소수점 실수로 반올림 했을 때, 상대 오차는 항상 엡실론 이하이다
```


```python
#
import sys
abs(a - b) <= sys.float_info.epsilon
```




    True




```python
# 3. python 3.5부터 활용 가능한 math 모듈을 통해 처리하는 법을 알아봅시다.
```


```python
#
import math
math.isclose(a, b)
```




    True



### `complex` (복소수, complex numbers)

각각 실수로 표현되는 실수부와 허수부를 가집니다.

복소수 z에서 이들 부분을 추출하려면 `z.real`과 `z.imag`를 사용합니다.

복소수는 허수부를 `j`로 표현합니다.


```python
# 변수에 복소수를 넣고 해당 변수의 type을 알아봅시다.
```


```python
#
a = 3 - 4j
type(a)
```




    complex




```python
# 복소수와 관련된 메소드들을 확인해봅시다.
```


```python
#
print(a.real)
print(a.imag)
print(a.conjugate())
```

    3.0
    -4.0
    (3+4j)
    


```python
# 문자열을 복소수로 변환해봅시다.
complex('1+2j')
```




    (1+2j)




```python
# 문자열을 변환할 때, 문자열은 중앙의 + 또는 - 연산자 주위에 공백을 포함해서는 안 됩니다.
complex('1 + 2j')
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-64-806b2631543b> in <module>
          1 # 문자열을 변환할 때, 문자열은 중앙의 + 또는 - 연산자 주위에 공백을 포함해서는 안 됩니다.
    ----> 2 complex('1 + 2j')
    

    ValueError: complex() arg is a malformed string


## bool

파이썬에는 `True`와 `False`로 이뤄진 `bool` 타입이 있습니다.

비교/논리 연산을 수행 등에서 활용됩니다.

다음은 `False`로 변환됩니다.
```
0, 0.0, (), [], {}, '', None
```


```python
# True와 False의 타입들을 알아봅시다.
```


```python
#
print(type(True))
print(type(False))
```

    <class 'bool'>
    <class 'bool'>
    


```python
# 다양한 True, False 상황들을 확인해봅시다.
# 형변환(Type Conversion)에서 추가적으로 다루는 내용입니다.
```


```python
#
bool(None)
```




    False




```python
#
bool(0.0)
```




    False




```python
#
bool(0)
```




    False




```python
#
bool(())
```




    False




```python
#
bool([])
```




    False




```python
#
bool({})
```




    False




```python
#
bool('')
```




    False



## None

파이썬에서는 값이 없음을 표현하기 위해 `None` 타입이 존재합니다.


```python
# None의 타입을 알아봅시다.
```


```python
#
type(None)
```




    NoneType




```python
# 변수에 저장해서 확인해봅시다.
```


```python
#
a = None
type(a)
```




    NoneType



## 문자형(String)

### 기본 활용법

* 문자열은 Single quotes(`'`)나 Double quotes(`"`)을 활용하여 표현 가능하다.

    - 작은따옴표: `'"큰" 따옴표를 담을 수 있습니다'`

    - 큰따옴표: `"'작은' 따옴표를 담을 수 있습니다"`

    - 삼중 따옴표: `'''세 개의 작은따옴표'''`, `"""세 개의 큰따옴표"""`


* 단, 문자열을 묶을 때 동일한 문장부호를 활용해야하며, `PEP-8`에서는 **하나의 문장부호를 선택**하여 유지하도록 하고 있다. 
(Pick a rule and Stick to it)


```python
# 변수에 문자열을 넣고 출력해봅시다.
```


```python
#
greetings = 'Hi'
name = 'SSAFY'
print(greetings, name)
print(type(greetings))
```

    Hi SSAFY
    <class 'str'>
    


```python
# 사용자에게 받은 입력은 기본적으로 str입니다.
```


```python
#
age = input()
print(type(age))
```

    28
    <class 'str'>
    

**따옴표 사용**

문자열 안에 문장부호(`'`, `"`)가 사용될 경우 이스케이프 문자(`\`)를 활용 가능 합니다. 


```python
# 문자열 안에 문장부호를 활용해서 오류를 확인해봅시다.
```


```python
#
print('철수가 말했다. '안녕?'')
```


      File "<ipython-input-90-bd809d21bc2d>", line 2
        print('철수가 말했다. '안녕?'')
                          ^
    SyntaxError: invalid syntax
    



```python
# 오류를 이스케이프 문자와 서로 다른 문장부호를 통해 해결해봅시다.
```


```python
#
print('철수가 말했다. "안녕?"')

print('철수가 말했다. \"안녕?\"')
```

    철수가 말했다. "안녕?"
    철수가 말했다. "안녕?"
    

여러줄에 걸쳐있는 문장은 다음과 같이 표현 가능합니다.

* `PEP-8`에 따르면 이 경우에는 반드시 `"""`를 사용하도록 되어 있다.


```python
# 여러줄을 출력해봅시다.
```


```python
#

```


```python
# 문자열은 + 연산자로 이어붙이고, * 연산자로 반복시킬 수 있습니다.
```


```python
#
prefix = 'Py'
prefix + 'thon'
```




    'Python'




```python
#
3 * 'hey' + 'yo!'
```




    'heyheyheyyo!'




```python
# 두 개 이상의 문자열이 연속해서 나타나면 자동으로 이어 붙여집니다.
```


```python
##
prefix = 'Py'
prefix + 'thon'
```




    'Python'



### 이스케이프 시퀀스

문자열을 활용하는 경우 특수문자 혹은 조작을 하기 위하여 사용되는 것으로 `\`를 활용하여 이를 구분합니다. 

|<center>예약문자</center>|내용(의미)|
|:--------:|:--------:|
|\n|줄 바꿈|
|\t|탭|
|\r|캐리지리턴|
|\0|널(Null)|
|\\\\|`\`|
|\\'|단일인용부호(`'`)|
|\\"|이중인용부호(`"`)|


```python
# 이스케이프 문자열을 조합하여 프린트해봅시다.
```


```python
#
print('이 다음은.\n 그리고 탭\t탭')
```

    이 다음은.
     그리고 탭	탭
    


```python
# print를 하는 과정에서도 이스케이프 문자열을 활용 가능합니다.
```


```python
#
print('내용을 띄워서 출력하고 싶으면?', end='\t')
print('옆으로 띄워짐')

print('내용을 띄워서 출력하고 싶으면?')
print('옆으로 띄워짐')
```

    내용을 띄워서 출력하고 싶으면?	옆으로 띄워짐
    내용을 띄워서 출력하고 싶으면?
    옆으로 띄워짐
    


```python
# 물론, end 옵션은 이스케이프 문자열이 아닌 다른 것도 가능합니다.
```


```python
#
print('개행 문자 말고도 가능합니다', end='!')
print('진짜로', end='!')
print('알고보면 print는 기본이 \\n', end='!')
```

    개행 문자 말고도 가능합니다!진짜로!알고보면 print는 기본이 \n!

### String interpolation 

* `%-formatting` 

* [`str.format()` ](https://pyformat.info/)

* [`f-strings`](https://www.python.org/dev/peps/pep-0498/) : 파이썬 3.6 이후 버전에서 지원


```python
# name 변수에 이름을 입력해봅시다.
```


```python
#
name = 'Kim'
```


```python
# %-formatting을 활용해봅시다.
```


```python
#
print('Hello, %s' % name)
```

    Hello, Kim
    


```python
# str.format()을 활용해봅시다.
```


```python
#
print('Hello, {}'.format(name))
```

    Hello, Kim
    


```python
# f-string을 활용해봅시다.
```


```python
#
print(f'Hello,{name}')
```

    Hello,Kim
    


```python
#
print(f"""
Hello,
{name}
""")
```

    
    Hello,
    Kim
    
    

* f-strings에서는 형식을 지정할 수 있다.


```python
# 다양한 형식을 활용하기 위해 datetime 모듈로 오늘을 표현해봅시다.
```


```python
#
import datetime
today = datetime.datetime.now()
print(today)
```

    2020-01-20 16:17:15.446206
    


```python
#
f'오늘은 {today:%Y}년 {today:%m}월 {today:%d}일 {today:%A}'
```




    '오늘은 2020년 01월 20일 Monday'



* f-strings에서는 연산과 출력형식 지정도 가능하다.


```python
# string interpolation에서 연산과 숫자 출력형식을 지정해봅시다.
```


```python
#
pi = 3.141592
f'원주율은 {pi:.4}. 반지름이 2일때 원의 넓이는 {pi*2*2}'
```




    '원주율은 3.142. 반지름이 2일때 원의 넓이는 12.566368'




```python
# 해당 문자/숫자 옆에 공백을 둘 수 있다.
number = 12345

print(f'{number:50}')
```

                                                 12345
    

# 연산자

## 산술 연산자
Python에서는 기본적인 사칙연산이 가능합니다. 

|연산자|내용|
|----|---|
|+|덧셈|
|-|뺄셈|
|\*|곱셈|
|/|나눗셈|
|//|몫|
|%|나머지(modulo)|
|\*\*|거듭제곱|

- 나눗셈 (`/`) 은 항상 float를 돌려준다.
- 정수 나눗셈 으로 (소수부 없이) 정수 결과를 얻으려면 `//` 연산자를 사용한다.



```python
# 2의 1000승을 확인해봅시다.
```


```python
#
2**1000
```




    10715086071862673209484250490600018105614048117055336074437503883703510511249361224931983788156958581275946729175531468251871452856923140435984577574698574803934567774824230985421074605062371141877954182153046474983581941267398767559165543946077062914571196477686542167660429831652624386837205668069376




```python
# 나눗셈과 관련된 산술연산자를 활용해봅시다.
```


```python
#
print(5/2)
print(5//2)
print(int(5/2))
print(5%2)
```

    2.5
    2
    2
    1
    


```python
# divmod는 나눗셈과 관련된 함수입니다.
```


```python
#
print(divmod(5, 2))
qoutient, remainder = divmod(5, 2)
print(f'5를 2로 나눈 몫은 {qoutient}이고 나머지는 {remainder}입니다.')
```

    (2, 1)
    5를 2로 나눈 몫은 2이고 나머지는 1입니다.
    


```python
# 음수 양수 표현도 해봅시다.
```


```python
#
positive_num = 4
negative_num = -2
print(positive_num, negative_num)
```

    4 -2
    

## 비교 연산자

우리가 수학에서 배운 연산자와 동일하게 값을 비교할 수 있습니다.

|연산자|내용|
|----|---|
|`<`|미만|
|`<=`|이하|
|`>`|초과|
|`>=`|이상|
|`==`|같음|
|`!=`|같지않음|
|`is`|객체 아이덴티티|
|`is not`|부정된 객체 아이덴티티|



```python
# 숫자의 대소관계를 비교해봅시다.
```


```python
#
3 > 6
```




    False




```python
# 같은 숫자인지 확인해봅시다.
```


```python
#
3 is 6
```




    False




```python
# 다른 숫자인지 확인해봅시다.
```


```python
#
3 == 3
```




    True




```python
# 문자열도 같은지 확인해봅시다.
```


```python
#
'Hi' == 'hi'
```




    False




```python
# is not 연산을 활용해봅시다.
```


```python
#
name = 'Luke'
if name is not None:
    print(f'{name}님이 입장하였습니다.')
```

    Luke님이 입장하였습니다.
    

## 논리 연산자

|연산자|내용|
|---|---|
|a and b|a와 b 모두 True시만 True|
|a or b|a 와 b 모두 False시만 False|
|not a|True -> False, False -> True|

우리가 보통 알고 있는 `&` `|`은 파이썬에서 비트 연산자입니다.


```python
# and과 관련해서 모든 case를 출력해봅시다.
```


```python
#
print(True and True)
print(True and False)
print(False and True)
print(False and False)
```

    True
    False
    False
    False
    


```python
# or과 관련해서 모든 case를 출력해봅시다.
```


```python
#
print(True or True)
print(True or False)
print(False or True)
print(False or False)
```

    True
    True
    True
    False
    


```python
# not을 활용해봅시다.
```


```python
#
print(not True)
print(not 0)
print(not False)
print(not 1)
```

    False
    True
    True
    False
    

* 파이썬에서 and는 a가 거짓이면 a를 리턴하고, 참이면 b를 리턴한다.
* 파이썬에서 or은 a가 참이면 a를 리턴하고, 거짓이면 b를 리턴한다.

### 단축평가
* 첫 번째 값이 확실할 때, 두 번째 값은 확인 하지 않음
* 조건문에서 뒷 부분을 판단하지 않아도 되기 때문에 속도 향상


```python
# 둘 다 true여야 하므로 뒷 값을 확인하기에 뒷 값이 나옴
'python' and 'javascript'
```




    'javascript'




```python
# 하나만 true면 되므로 앞 값이 나옴
'python' or 'javascript'
```




    'python'




```python
vowels = 'aeiou'
```


```python
# vowels 안에 'b'가 없으므로 False
('a' and 'b') in vowels
```




    False




```python
#
('b' and 'a') in vowels
```




    True




```python
#
'a' and 'b'
```




    'b'




```python
#
'a' or 'b'
```




    'a'



- `and` 는 둘 다 True일 경우만 True이기 때문에 첫번째 값이 True라도 두번째 값을 확인해야 하기 때문에 'b'가 반환된다.
- `or` 는 하나만 True라도 True이기 때문에 True를 만나면 해당 값을 바로 반환한다.


```python
# and의 단축평가(short-circuit evaluation)에 대해서 알아봅시다.
```


```python
# 0 : False
print(3 and 5)
print(3 and 0)
print(0 and 5)
print(0 and 0)
```

    5
    0
    0
    0
    


```python
# or의 단축평가(short-circuit evaluation)에 대해서 알아봅시다.
```


```python
# 0 : False, or : 1개만 true면 되니까 true 값을 도출
print(3 or 5)
print(3 or 0)
print(0 or 5)
print(0 or 0)
```

    3
    3
    5
    0
    

## 복합 연산자

복합 연산자는 연산과 대입이 함께 이뤄집니다. 

가장 많이 활용되는 경우는 반복문을 통해서 개수를 카운트하거나 할 때 활용됩니다.

|연산자|내용|
|----|---|
|a += b|a = a + b|
|a -= b|a = a - b|
|a \*= b|a = a \* b|
|a /= b|a = a / b|
|a //= b|a = a // b|
|a %= b|a = a % b|
|a \*\*= b|a = a ** b|


```python
# 복합연산자는 이럴 때 사용됩니다. 
```


```python
#
cnt = 0

while cnt < 5:
    print(cnt)
    cnt += 1 # cnt = cnt + 1
```

    0
    1
    2
    3
    4
    

## 기타 연산자

### Concatenation

숫자가 아닌 자료형은 `+` 연산자를 통해 합칠 수 있습니다.


```python
# 문자열을 더해봅시다.(합쳐봅시다.)
```


```python
#
'hi, ' + 'Judy'
```




    'hi, Judy'




```python
# list를 더해봅시다.(합쳐봅시다.)
```


```python
#
[1, 2, 3] + [4, 5, 6]
```




    [1, 2, 3, 4, 5, 6]



### Containment Test

- `in` 연산자를 통해 요소가 속해있는지 여부를 확인할 수 있습니다.


```python
# 문자열안에 특정한 문자가 있는지 확인해봅시다.
```


```python
#
'a' in 'apple'
```




    True




```python
# 
'b' in 'apple'
```




    False




```python
# list안에 특정한 원소가 있는지 확인해봅시다.
```


```python
#
1 in [1, 2, 3]
```




    True




```python
# range안에 특정한 원소가 있는지 확인해봅시다.
```


```python
#
1 in range(5)
```




    True



### Identity

`is` 연산자를 통해 동일한 object인지 확인할 수 있습니다. 

* (Class를 배우고 다시 학습)


```python
# 파이썬에서 -5 부터 256 까지의 id는 동일합니다.
```


```python
#
a = 3
b = 3
a is b
```




    True




```python
# 257 이후의 id 는 다릅니다.
```


```python
#
a = 257
b = 257
a is b

print(id(a))
print(id(b))
```

    3115238416112
    3115238416048
    

### Indexing/Slicing
`[]`를 통한 값을 접근하고, `[:]`을 통해 리스트를 슬라이싱할 수 있습니다.

* (다음 챕터를 배우면서 추가 학습)


```python
# 문자열을 인덱싱을 통해 값에 접근해봅시다.
```


```python
# indexing 
'hi'[0]
```




    'h'




```python
'hi'[0] = 7
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-207-aa9c0cd7b542> in <module>
    ----> 1 'hi'[0] = 7
    

    TypeError: 'str' object does not support item assignment



```python
[1, 2, 3][0] = 7
```


```python
# slicing
[1, 2, 3, 4, 5][0:3]
```




    [1, 2, 3]




```python
[1, 2, 3, 4, 5][1:4]
```




    [2, 3, 4]




```python
# list slicing
numbers = [1, 2, 3, 4, 5]
```


```python
#
a = numbers[-1:]
b = numbers[0:-1]
c = numbers[0:4:2]

print(a)
print(b)
print(c)
```

    [5]
    [1, 2, 3, 4]
    [1, 3]
    

## 연산자 우선순위

0. `()`을 통한 grouping

1. Slicing

2. Indexing

3. 제곱연산자
    `**`

4. 단항연산자 
    `+`, `-` (음수/양수 부호)

5. 산술연산자
    `*`, `/`, `%`
    
6. 산술연산자
    `+`, `-`
 
7. 비교연산자, `in`, `is`

8. `not`

9. `and` 

10. `or`


```python
# 우선순위를 확인해봅시다.
```


```python
#
-3**6
```




    -729




```python
#
(-3)**6
```




    729




```python
# 다음 결과는 어떻게 나올까요? 실행하기 전에 충분히 고민하고 실행해 봅시다.
(1 + 2)**2 and 0 in [1, 2, 3] 
```




    False



# 기초 형변환(Type conversion, Typecasting)

<img width="708" alt="typecasting" src="https://user-images.githubusercontent.com/18046097/61180466-a6a67780-a651-11e9-8c0a-adb9e1ee04de.png">



파이썬에서 데이터타입은 서로 변환할 수 있습니다.

## 암시적 형변환(Implicit Type Conversion)
사용자가 의도하지 않았지만, 파이썬 내부적으로 자동으로 형변환 하는 경우입니다.
아래의 상황에서만 가능합니다.
* bool
* Numbers (int, float, complex)


```python
# boolean과 integer는 더할 수 있을까요?
```


```python
#
True + 3
```




    4




```python
# int, float, complex를 각각 변수에 대입해봅시다.
```


```python
#
int_number = 3
float_number = 5.0
complex_number = 3+5j
```


```python
# int와 float를 더해봅시다. 그 결과의 type은 무엇일까요?
```


```python
#type conversion -> float
print(int_number + float_number)
print(type(int_number + float_number))
```

    8.0
    <class 'float'>
    


```python
# int와 complex를 더해봅시다. 그 결과의 type은 무엇일까요?
```


```python
#type conversion -> complex
print(int_number + complex_number)
print(type(int_number + complex_number))
```

    (6+5j)
    <class 'complex'>
    

## 명시적 형변환(Explicit Type Conversion)
위의 상황을 제외하고는 모두 명시적으로 형 변환을 해주어야합니다.

* string -> intger  : 형식에 맞는 숫자만 가능
* integer -> string : 모두 가능

암시적 형변환이 되는 모든 경우도 명시적으로 형변환이 가능합니다.

* `int()` : string, float를 int로 변환
* `float()` : string, int를 float로 변환
* `str()` : int, float, list, tuple, dictionary를 문자열로 변환

`list()`, `tuple()` 등은 다음 챕터에서 배울 예정입니다.


```python
# integer와 string 사이의 관계는 명시적으로 형변환을 해줘야만 합니다.
```


```python
1 + '등'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-18-67e0330e0b9e> in <module>
    ----> 1 1 + '등'
    

    TypeError: unsupported operand type(s) for +: 'int' and 'str'



```python
#
str(1) + '등'
```




    '1등'




```python
# string 3을 integer로 변환해봅시다.
```


```python
#
a = '3'
int(a)
```




    3




```python
# string 3.5를 float로 변환해봅시다.
```


```python
#
a = '3.5'
float(a)
```




    3.5




```python
# string은 글자가 숫자일때만 형변환이 가능합니다.
```


```python
#
a = 'hi'
int(a)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-24-3d0cceaab003> in <module>
          1 #
          2 a = 'hi'
    ----> 3 int(a)
    

    ValueError: invalid literal for int() with base 10: 'hi'



```python
a = 3
str(a)
```




    '3'




```python
# string 3.5를 int로 변환할 수는 없습니다.
```


```python
#
a = '3.5'
int(a)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-29-d943675fc7e7> in <module>
          1 #
          2 a = '3.5'
    ----> 3 int(a)
    

    ValueError: invalid literal for int() with base 10: '3.5'



```python
# float 3.5는 int로 변환이 가능합니다.
```


```python
#
a = 3.5
int(a)
```




    3



# 시퀀스(sequence) 자료형

`시퀀스`는 데이터가 순서대로 나열된 형식을 나타냅니다. 

* **주의! 순서대로 나열된 것이 `정렬되었다`라는 뜻은 아니다.**

파이썬에서 기본적인 **시퀀스** 타입은 다음과 같습니다.

* 리스트(list)

* 튜플(tuple)

* 레인지(range)

* 문자열(string)

* 바이너리(binary) : 따로 다루지는 않습니다.



## `list`

<center><img src="https://user-images.githubusercontent.com/18046097/61180421-fe90ae80-a650-11e9-8211-d06f87756d05.png", alt="list figure"/></center>

**활용법**
```python
[value1, value2, value3]
```

리스트는 대괄호`[]` 및 `list()` 를 통해 만들 수 있습니다.

값에 대한 접근은 `list[i]`를 통해 합니다.


```python
# 빈 리스트를 만들어봅시다.
```


```python
# 리스트는 두 가지 방법으로 만들 수 있습니다.
l = []
ll = list()
print(type(l))
print(type(ll))
```

    <class 'list'>
    <class 'list'>
    


```python
# 원소를 포함한 리스트를 만들어봅시다.
```


```python
#
locations = ['서울', '대전', '광주', '구미']
print(locations)
print(type(locations))
```

    ['서울', '대전', '광주', '구미']
    <class 'list'>
    


```python
# 첫번째 값에 접근해봅시다.
```


```python
#
locations[0]
```




    '서울'




```python
# 리스트의 요소 값을 변경해봅시다
locations[0] = '뉴욕'
print(locations)
```

    ['뉴욕', '대전', '광주', '구미']
    


```python
# 순서가 있다는 것이 정렬된 것을 의미하는 것은 아닙니다.
```


```python
#
numbers = [5, 3, 4, 1]
```

## `tuple`

**활용법**
```python
(value1, value2)
```

튜플은 리스트와 유사하지만, `()`로 묶어서 표현합니다.

그리고 tuple은 수정 불가능(불변, immutable)하고, 읽을 수 밖에 없습니다.

직접 사용하기 보다는 **파이썬 내부**에서 사용하고 있습니다.


```python
# tuple을 만들어봅시다.
```


```python
#
tuple_ex = (1, 2)
print(type(tuple_ex))
```

    <class 'tuple'>
    


```python
# 아래와 같이 만들 수도 있습니다.
```


```python
# 괄호 생략 가능
tuple_ex2 = 1, 2
print(tuple_ex2)
print(type(tuple_ex2))
```

    (1, 2)
    <class 'tuple'>
    


```python
# 파이썬 내부에서는 다음과 같이 활용됩니다.
# 앞선 2. 변수 및 자료형 예제에서 사용된 코드입니다.
```


```python
#
x, y = 1, 2
print(x)
print(y)
```

    1
    2
    


```python
# 실제로는 tuple로 처리됩니다.
```


```python
#
x, y = (1, 2)
print(x)
print(y)
```

    1
    2
    


```python
# 변수의 값을 swap하는 코드 역시 tuple을 활용하고 있습니다. 
```


```python
#
x, y = y, x
print(x)
print(y)
```

    2
    1
    


```python
# 빈 튜플은 빈 괄호 쌍으로 만들어집니다.
```


```python
#
empty = ()
print(empty)
print(type(empty))
```

    ()
    <class 'tuple'>
    


```python
# 하나의 항목으로 구성된 튜플은 값 뒤에 쉼표를 붙여서 만듭니다.
```


```python
#
single_tuple = ('hello', )
print(type(single_tuple))
print(len(single_tuple))
```

    <class 'tuple'>
    1
    


```python
# 이렇게 ,를 붙이지 않으면 숫자가 됩니다.
```


```python
#
numbers = (1)
print(numbers)
print(type(numbers))
```

    1
    <class 'int'>
    


```python
# tuple은 요소값을 변경할 수 없습니다. (immutable)
```


```python
# 
list_numbers = [1, 2, 3, 4, 5]
print(list_numbers[0])
```

    1
    


```python
list_numbers[0] = 7
print(list_numbers[0])
```

    7
    


```python
# 순서가 있는 리스트라 가능
tuple_numbers = (1, 2, 3, 4, 5)
print(tuple_numbers[0])
```

    1
    


```python
tuple_numbers[0] = 2
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-64-558748f8b00b> in <module>
    ----> 1 tuple_numbers[0] = 2
    

    TypeError: 'tuple' object does not support item assignment


##  `range()`

`range` 는 숫자의 시퀀스를 나타내기 위해 사용됩니다.

기본형 : `range(n)` 


> 0부터 n-1까지 값을 가짐


범위 지정 : `range(n, m)` 

> n부터 m-1까지 값을 가짐

범위 및 스텝 지정 : `range(n, m, s)`

> n부터 m-1까지 +s만큼 증가한다


```python
# range를 만들어봅시다.
```


```python
#
type(range(2))
```




    range




```python
# range는 range 객체를 return 하기 때문에 우리가 익히 알고 있는 자료형으로 변환해야 합니다. 
# 뒤에서 추가 학습
```


```python
#
print(tuple(range(5)))
print(list(range(5)))
```

    (0, 1, 2, 3, 4)
    [0, 1, 2, 3, 4]
    


```python
# range에 담긴 값을 list로 바꿔서 확인해봅시다.
```


```python
#
numbers = list(range(10))
print(numbers)
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    


```python
# 4 ~ 8까지의 숫자를 담은 range를 list로 만들어봅시다.
```


```python
#
list(range(4, 9))
```




    [4, 5, 6, 7, 8]




```python
# 0부터 -9까지 담긴 range를 list로 만들어봅시다.
```


```python
#
list(range(0, -10, -1))
```




    [0, -1, -2, -3, -4, -5, -6, -7, -8, -9]




```python
# range 함수는 반복, 인덱싱(슬라이싱), len()함수만 지원함
# 그 외의 시퀀스 연산은 지원하지 않음
```


```python
# 인덱싱/슬라이싱 [::-1] : 역순
list(range(9)[::-1])
```




    [8, 7, 6, 5, 4, 3, 2, 1, 0]




```python
for i in range(6)[::-1]:
    print(i)
```

    5
    4
    3
    2
    1
    0
    


```python
len(range(6))
```




    6




```python
list(range(6))
```




    [0, 1, 2, 3, 4, 5]




## 시퀀스에서 활용할 수 있는 연산자/함수 

|operation|설명|
|---------|---|
|x `in` s	|containment test|
|x `not in` s|containment test|
|s1 `+` s2|concatenation|
|s `*` n|n번만큼 반복하여 더하기
|`s[i]`|indexing|
|`s[i:j]`|slicing|
|`s[i:j:k`]|k간격으로 slicing|
|len(s)|길이|
|min(s)|최솟값|
|max(s)|최댓값|
|s.count(x)|x의 개수|


```python
# contain test를 확인해봅시다.
```


```python
#
s = 'string'
print('a' not in s)
print('a' in s)
```

    True
    False
    


```python
#
l = [1, 2, 3, 5, 1]
print(3 in l)
```

    True
    


```python
# concatenation(연결, 연쇄)를 해봅시다.
```


```python
#
print('안녕' + '하세염')
print((1, 2) + (5, 6))
print([1, 2] + [5, 6])
```

    안녕하세염
    (1, 2, 5, 6)
    [1, 2, 5, 6]
    


```python
# 숫자 0이 6개 있는 list를 만들어봅시다.
```


```python
#
[0] * 6
```




    [0, 0, 0, 0, 0, 0]




```python
# indexing과 slicing을 하기 위해 list하나를 만들어주세요.
```


```python
#
location = ['서울', '대전', '구미', '광주']
location[1]
location[3]
```




    '광주'




```python
# 두번째, 세번째 값만 가져와봅시다.
```


```python
#
location[1:3]
```




    ['대전', '구미']




```python
# 0부터 30까지의 숫자를 3씩 증가시킨 리스트로 만들어봅시다.
```


```python
#
sample_list = list(range(0, 31, 3))
print(sample_list)
```

    [0, 3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
    


```python
# : 슬라이싱
sample_list = list(range(0, 31))
test_list = sample_list[0:len(sample_list):3]
print(test_list)
```

    [0, 3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
    


```python
# 위에서 만든 list의 길이를 확인해봅시다.
```


```python
#
len(test_list)
```




    11




```python
# 위에서 만든 list의 최솟값, 최댓값을 확인해봅시다.
```


```python
#
print(max(test_list))
print(min(test_list))
```

    30
    0
    


```python
# list에 담긴 특정한 것의 개수를 확인할 수도 있습니다.
```


```python
#
sample_list = [1, 2, 1, 3, 1, 5]
sample_list.count(1)
```




    3




```python
# slicing을 한번만 더 연습해 봅시다.
numbers = [1, 2, 3, 4, 5, 6]
```


```python
# numbers를 slicing해 [1, 2, 3]이라는 새로운 리스트를 반환하세요
sliced_list = numbers[0:3]
print(sliced_list)
```

    [1, 2, 3]
    


```python
# numbers를 slicing해 [1, 3, 5]라는 새로운 리스트를 반환하세요.
sliced_list = numbers[::2]
print(sliced_list)
```

    [1, 3, 5]
    

# set, dictionary

`set`은 순서가 없는 자료구조입니다.

`dictionary`는 아이템이 삽입되는 순서를 가지고 있습니다.

## `set`

* 세트는 수학에서의 집합과 동일하게 처리된다. 

* 세트는 중괄호`{}`를 통해 만들며, 순서가 없고 중복된 값이 없다.

* 빈 집합을 만들려면 `set()`을 사용해야 합니다. `{}`로 사용 불가능.

**활용법**
```python
{value1, value2, value3}
```

|연산자/함수|설명|
|---|---|
|a `-` b|차집합|
|a `\|` b|합집합|
|a `&` b|교집합|
|a`.difference(b)`|차집합|
|a`.union(b)`|합집합|
|a`.intersection(b)`|교집합|


```python
# set 두개를 만들어서 연산자들을 활용해봅시다.
```


```python
#
set_a = {1, 2, 3}
set_b = {3, 6, 9}
print(set_a - set_b)
print(set_a | set_b)
print(set_a & set_b)
```

    {1, 2}
    {1, 2, 3, 6, 9}
    {3}
    


```python
# set은 중복된 값이 있을 수 없습니다.
```


```python
#
set_c = {1, 1, 1}
print(set_c)
```

    {1}
    

* `set`을 활용하면 `list`의 중복된 값을 손쉽게 제거할 수 있습니다.


```python
# set으로 중복된 값을 제거해봅시다.
```


```python
#
list_a = [1, 2, 3, 1, 1, 2]
set_a = set(list_a)
print(set_a)
```

    {1, 2, 3}
    


```python
# 다시 list로 바꿔서 확인해봅시다.
```


```python
#
list(set_a)
```




    [1, 2, 3]



## `dictionary`

<center><img src="https://user-images.githubusercontent.com/18046097/61180427-1405d880-a651-11e9-94e1-1cc5c2a2ff34.png"></center> 

**활용법**
```python
{Key1:Value1, Key2:Value2, Key3:Value3, ...}
```

* 딕셔너리는 `key`와 `value`가 쌍으로 이뤄져있으며, 궁극의 자료구조이다. 
* `{}`를 통해 만들며, `dict()`로 만들 수도 있다.
* `key`는 불변(immutable)한 모든 것이 가능하다. (불변값 : string, integer, float, boolean, tuple, range)
* `value`는 `list`, `dictionary`를 포함한 모든 것이 가능하다.


```python
#참고 key는 immutable한 객체만 가능

sample_dict = {
    'justin' : 'pizza' # string은 수정 불가능(immutable)하기 때문에 key로 사용 가능
}
sample_dict
```




    {'justin': 'pizza'}




```python
#참고  key는 mutable한 객체는 불가능

sample_dict = {
    [1, 2, 3]: 'numbers' # list는 수정 가능(mutable)하기 때문에 key로 사용 불가능
}
sample_dict
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-128-e8b58d1f60cc> in <module>
          2 
          3 sample_dict = {
    ----> 4     [1, 2, 3]: 'numbers'
          5 }
          6 sample_dict
    

    TypeError: unhashable type: 'list'



```python
# 비어있는 dictionary를 두가지 방법으로 만들어봅시다.
```


```python
#
dict_a = {a, }
print(type(dict_a))
dict_b = dict()
print(type(dict_b))
```

    <class 'set'>
    <class 'dict'>
    


```python
# dictionary는 중복된 key는 존재할 수가 없습니다. 중복되면 마지막 key로 덮어씁니다.
```


```python
#
dict_a = {1: 1, 2: 2, 3: 3, 1: 4}
print(dict_a)
```

    {1: 4, 2: 2, 3: 3}
    


```python
# 지역번호(서울-02 경기-031 경북-054)가 담긴 전화번호부를 만들어봅시다.
```


```python
#
phone_book = {
    '서울': '02',
    '경기': '031',
    '경북': '054'
}
print(phone_book)
```

    {'서울': '02', '경기': '031', '경북': '054'}
    


```python
# 딕셔너리의 .keys() 메소드를 활용하여 key를 확인 해볼 수 있습니다.
```


```python
#
phone_book.keys()
```




    dict_keys(['서울', '경기', '경북'])




```python
# 딕셔너리의 .values() 메소드를 활용하여 value를 확인 해볼 수 있습니다.
```


```python
#
phone_book.values()
```




    dict_values(['02', '031', '054'])




```python
# 딕셔너리의 .items() 메소드를 활용하여 key, value를 확인 해볼 수 있습니다.
```


```python
#
phone_book.items()
```




    dict_items([('서울', '02'), ('경기', '031'), ('경북', '054')])




```python
# 아래와 같은 방법으로 활용 할 수 있습니다.
```


```python
# 
for location, phone in phone_book.items():
    print(location, phone)
```

    서울 02
    경기 031
    경북 054
    

# 정리
## 데이터 타입
<center><img src="https://user-images.githubusercontent.com/18046097/61180439-44e60d80-a651-11e9-9adc-e60fa57c2165.png", alt="container"/></center>
