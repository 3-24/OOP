[TOC]

<div style="page-break-after: always;"></div>

> Python is **Interpreter language**!

Python 2와 다르게, int / int 는 자료형이 float이다.

Error 종류

* Syntax error: Python cannot understand your program, and refuses to execute it.
* Runtime error: When executing your program (at runtime), your program suddenly terminates with an error message.
* Semantic error: Your program runs without error messages but does not do what it is supposed to do.

print 함수

```
print(...)
    print(value, ..., sep=' ', end='\n')

    Optional keyword arguments:
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
```



# 1. Exceptions

Python이 처리할 수 없는 부분을 만나면 exception을 raise한다. exception 종류는 아주 많으니까 여기서는 다루지 않는다.

## 2.1. Handling Exceptions

```text
try:
	operations
except ExceptionI:
	if excetionI raised, execute this block.
except ExceptionII:
	if excetionII raised, excute this block.
else:
	otherwise, excute this block.
```



# 3. Ternary Operator

삼항연산자

```python
true-expression if condition else false-expression
```

이 구문은 다음과 같은 일반적인 if-else statement와 동일하다.

```python
if condition:
	true-expression
else:
	false-expression
```



# 4. Namespace

프로그램에 사용되는 name들이 충돌없이 관리되도록 하는 시스템

## 4.1. Scope

name이 유효한 범위.

Local < Enclosed < Global < Built-Ins

### 4.1.1. Local

Names assigned in any way within a function (`def` or `lambda`)), and not declared global in that function.

### 4.1.2. Enclosed

Name in the local scope of any and all statically enclosing functions (`def` or `lambda`), from inner to outer.

### 4.1.3. Global

Names assigned at the top-level of a module file, or by executing a `global` statement in a `def` within the file.

### 4.1.4. Built-Ins

Names preassigned in the built-in names module : `open`,`range`,`SyntaxError`,...

[Reference](https://stackoverflow.com/questions/291978/short-description-of-the-scoping-rules)



# 5. String

iterable, ***immutable*** object!

## 5.1. Class Functions

* upper(), lower()

```python
>>> s = 'abcDEF1234'
>>> s.upper()
'ABCDEF1234'
```

* startswith(prefix), endswith(suffix)

* find(str,start,end) : return the string index of str as the first substring of s (-1 if not substring)

  rfind(str,start,end) : in reverse order

  index(str,start,end) : If there is no index, return error

  rindex(str, start, end) : in reverse order

* center(width,fillchar)

```python
>>> a = 'hello world'
>>> print(a.center(17,'_'))
___hello world___
>>> print(a.center(18,'_'))
___hello world____
```

* ljust(width,fillchar) : left-justified fill

  rjust(width,fillchar) : right-justified fill

  zfill(width) : fill zero, equivalent to ljust(width,'0').

```python
>>> s = '____'
>>> s.ljust(10,'=')
'____======'
>>> s.rjust(10,'=')
'======____'
```

* strip(), lstrip(), rstrip()

* join(str)

```python
>>> s = '1234'
>>> 'X'.join(s)
'1X2X3X4'
```

* count(sub,start,end)

* startswith(prefix,start,end), endswith(suffix,start,end)

```Python
>>> s = '123'
>>> s.startswith('1')
True
>>> s.startswith('12')
True
>>> s.startswith('2')
False
```

* split(sep)

  splitlines(bool)

* partition(sep)

  rpartition(sep)

```python
>>> a = "Object Oriented\t Programming\nPython\n"
>>> a.splitlines(False)
['Object Oriented\t Programming', 'Python']
>>> a.splitlines(True)
['Object Oriented\t Programming\n', 'Python\n']
>>> a.split()
['Object', 'Oriented', 'Programming', 'Python']
>>> a.partition('e')
('Obj', 'e', 'ct Oriented\t Programming\nPython\n')
```

* replace(old,new,count)

* expandtabs(tabsize) : equivalent to replace('\t', tabsize).
  isalnum(), isalpha(), isdigit(), isspace(), isupper(), islower(), istitle()

```python
>>> a = '_\t_\t_\n'
>>> a.expandtabs(6)
'_     _     _\n
```
```python
>>> s = 'Nodos Vedos'
>>> s.isalpha()
False
>>> s = '\t    \n'
>>> s.isspace()
True
>>> s = '214151531W'
>>> s.isupper()
True
```
## 5.2. Formatted Output

기본 구조는 다음과 같다:

```Python
	'{} plain string.. {}'.format('','')
```
각 중괄호 안에 들어가는 문장을 형식화하면 이렇게 나누어진다.
```text
{:[align][minimum_width][.precision][descriptor]}
align: <(left), >(right), ^(center)
descripter
	s(string)
	d(decimal integer, error if float object is substituted)
	f(floating-point decimal)
	e(floating-point exponential)
	%(floating-point as percent	)
```
* alignment와 minimum_with의 조절

```python
>>> '_{:<20}__'.format('example string')
'_example string      __'
>>> '_{:>20}__'.format('example string')
'_      example string__'
>>> '_{:^20}__'.format('example string')
'_   example string   __'
>>> '_{:^19}__'.format('example string')
'_  example string   __'
```
* float descripter의 비교

```python
>>> num = 123456789.123456789
>>> '{:f} {:e} {:%}'.format(num,num,num)
'123456789.123457 1.234568e+08 12345678912.345678%'
```



# 6. List

iterable, mutable object.

## 6.1. Constructor

* list() : Only takes iterable object(list, tuple, string ... even dictionary!)

```python
>>> L = list({'a':1, 'b':2})
>>> print(L)
['a', 'b']
```

* [element 1, element 2, ...].

## 6.2. Operators

### 6.2.1. comparison

기본적으로 **사전식 비교**. 자료형이 다른 element를 비교할 때는 TypeError가 뜨니 주의하자.

사전식 비교로는 같지만, 길이가 다른 경우 길이가 더 큰 쪽이 크다.

```python
>>> [1,2,3,4] < [1,2,3,4,0]
True
```

## 6.3. Functions

* len()
* min(), max()
* sum()

## 6.4. Iteration

```python
for element in list:
	some_function(element)
```



## 6.5. Methods

### 6.5.1. non-Modifying Methods

* index(x)
* count(x)
* sorted()

### 6.5.2. Modifying Methods

* append(x) : list의 끝에 원소를 추가한다.
* pop(index) : L.pop(index)는 L[index]를 L에서 제거하고 그 값을 리턴한다. index가 입력으로 없다면 0으로 취급된다.
* extend(C) : list의 끝에 iterable한 collection C를 추가한다.

```python
>>> L = [1,2,3]
>>> L.extend((4,5,6))
>>> L
[1, 2, 3, 4, 5, 6]
```

* insert(index,object) : 입력된 object를 index에 삽입한다.
* remove(value) : 첫 번째로 나타나는 value를 제거한다. 없으면 ValueError.
* sort()
* reverse()

## 6.6. Multiple Assignment

element1, element2, element3 = [a,b,c]

만약 list 길이보다 적거나 많은 variable을 적는다면 ValueError.

## 6.7. References

list와 같은 iterable object를 다룰 때 가장 주의해야 하는 부분이다. 수업에서는 list에서만 다루었다.

```python
>>> a = [1,2,3]
>>> b = a
>>> a is b
True
>>> a.append(4)
>>> b
[1, 2, 3, 4]
```

### 6.7.1. Shallow Copy

slicing을 이용하는 방법.

```python
>>> a = [1,2,3]
>>> b = a[:]
>>> a is b
False
>>> a.append(4)
>>> b
[1, 2, 3]
```

하지만 2차원 이상의 list에서는 적용이 되지 않는다.

```python
>>> a = [1,2,3,[4,5,6]]
>>> b = a[:]
>>> a[3].append(7)
>>> b
[1, 2, 3, [4, 5, 6, 7]]
```

### 6.7.2. Deep Copy

```python
>>> a = [1,2,3,[4,5,6]]
>>> import copy
>>> b = copy.deepcopy(a)
>>> a[3].append(7)
>>> b
[1, 2, 3, [4, 5, 6]]
```

### 6.7.3. Self-Reference

```python
>>> a = [1,2,3]
>>> a.append(a)
>>> a
[1, 2, 3, [...]]
```

## 6.8. List Comprehension

`[expression for-clause condition]`

for문에서 뽑은 element가 condition을 만족하면 expression을 돌려서 반환값을 저장한다.

```python
# isPrime is a user-builted function that checks whether the input is prime.
>>> [(i,i**2) for i in [2,3,4,5,6,7,8,9,10,11,12,13,14,15] if isPrime(i)]
[(2, 4), (3, 9), (5, 25), (7, 49), (11, 121), (13, 169)]
```

ternary operator나 ~~lambda~~을 이용하면 더 다양한 list 구성이 가능하다.



# 7. Tuple

**immutable list**

modifying method를 사용하지 못한다는 점 외에는 list와 동일하다. 즉, sort()나 append()를 쓸 수 없다.



# 8. Dictionary

key와 그에 대응되는 value로 구성된 mutable, iterable object. 순서의 개념이 존재하지 않는다.

## 8.1. Constructor

* dict() : 새로운 빈 dictionary

* dict(mapping) : new dictionary initialized from a mapping object's (key, value) pairs

  * zip : create pairs from two parallel sequences

  ```python
  >>> keys = ['a','b','c']
  >>> values = [1,2,3]
  >>> dict(zip(keys,values))
  {'a': 1, 'b': 2, 'c': 3}
  ```


* dict(iterable) : 다음 코드를 실행한 결과와 같은 dict를 만든다.

  ```python
  d = {}
  for k, v in iterable:
  	d[k] = v
  ```

## 8.2. Class Functions

* items() : (key,value) 쌍으로 이루어진 set-like object
* keys() : key로 이루어진 set-like object
* values() : value로 이루어진 set-like object

```python
>>> D = {1:'a', 2:'b', 3:'c'}
>>> D.items()
dict_items([(1, 'a'), (2, 'b'), (3, 'c')])
>>> D.keys()
dict_keys([1, 2, 3])
>>> D.values()
dict_values(['a', 'b', 'c'])
```

* copy() : shallow copy를 return한다.



# 9. Set

수학의 집합과 비슷한 성질을 가지는 iterable object.

## 9.1. Constructor

* set() : new empty set object
* set(iterable)
* {element1, element2, ...}



## 9.2. Class Functions

* add(...)

* pop(...)

* remove(...) : element를 set에서 제거한다. 없으면 KeyError.

  discard(...) : 같은 역할을 하지만 없어도 KeyError가 뜨지 않는다.

* copy(...) : return shallow copy

* difference(...) : $ A \setminus B $.

  symmetric_difference(...) : $ (A \setminus B) \cup( B \setminus A) $

* intersection(...) : $ A \cap B $

* union(...) : $A \cup B $

* isdisjoint(...) 

* issubset(...) : 입력된 set 안에 있는가

* issuperset(...) : 입력된 set을 포함하는가





**끝내며**

구조는 객체지향프로그래밍 슬라이드들을 참고했지만 example 코드들은 직접 만들었습니다.

각 함수들의 설명은 뇌피셜+python의 help 함수를 가장 많이 참고했습니다.