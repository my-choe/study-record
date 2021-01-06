# 🍎 Python 예제 🍎

```python
# 1.
def all_unique(first) :
    return len(first) == len(set(first)) #set자료형은 중복값 제거
x = [1, 2, 3, 4, 5, 6]
y = [1, 2, 2, 3, 4, 5]
all_unique(x) # True
all_unique(y) # False

# 2. 앞글자를 대문자로
def capitalize_every_word(s) :
    return s.title()
capitalize_every_word('hello world!') # 'Hello World!'
# print(capitalize_every_word('hello world!'))

#3
def celsius_to_fahrenheit(celsius) :
    return((celsius * 1.8) + 32)
# print(celsius_to_fahrenheit(180)) #356.0

#4
# false, none 값 제거
def compact(first) :
    return list(filter(None, first))
# print(compact([0, 1, False, 2, '', 3, 'a', 's', 34])) #[1, 2, 3, 'a', 's', 34]

#5
# 주어진 값이 리스트에서 몇 개 있는지 확인
def count_occurrences(first, val) :
    return len([x for x in first if x == val and type(x) == type(val)])
# print(count_occurrences([1, 1, 2, 1, 2, 3], 1)) #3

#6
# degree를 radian으로 변환
from math import pi
def degrees_to_rads(deg) :
    return (deg * pi) / 180.0
# print(degrees_to_rads(180)) #3.141592653589793

#7 
# 두 리스트의 차집합 구하기
def difference(a, b):
    b = set(b)
    return [item for item in a if item not in b]
# print(difference([1, 2, 3], [1, 2, 4])) #[3]

#8
# 숫자를 자릿수 기준으로 리스트 만들기
def digitize(n):
    return list(map(int, str(n)))
# print(digitize(123)) #[1,2,3]

#9
# 왼쪽에서부터 n개의 값 제거
def drop(a, n = 1) :
    return a[n:]
# print(drop([1, 2, 3])) #[2, 3]
# print(drop([1, 2, 3], 2)) #[3]
# print(drop([1, 2, 3], 3)) #[]

#10
# 오른쪽에서부터 n개의 값 제거
def drop_right(a, n = 1) :
    return a[:-n]
# print(drop([1, 2, 3])) #[1, 2]
# print(drop([1, 2, 3], 2)) #[1]
# print(drop([1, 2, 3], 3)) #[]

#11
#리스트의 모든 n번째 값 반환
def every_nth(first, nth):
    return first[nth - 1::nth]
# print(every_nth([1, 2, 3, 4, 5, 6], 2)) #[2, 4, 6]

#12
#화씨온도에서 섭씨온도로 변환
def fahrenheit_to_celsius(fahrenheit):
    return ((fahrenheit - 32) / 1.8)
# print(fahrenheit_to_celsius(77)) #25.0

#13
#리스트에서 고유하지 않은 값 필터링
from collections import Counter
def filter_non_unique(first):
    return [item for item, count in Counter(first).items() if count == 1]
# print(filter_non_unique([1, 2, 2, 3, 4, 4, 5, 5])) # [1, 3]

#14
# 리스트에서 고유한 값 필터링
from collections import Counter
def filter_unique(first):
    return [item for item, count in Counter(first).items() if count > 1]
# print(filter_unique([1, 2, 2, 3, 4, 4, 5])) #[2, 4]

#15
# 리스트의 모든 값에 주어진 함수를 실행
def for_each(itr, fn):
    for el in itr:
        fn(el)
# for_each([1, 2, 3], print)

#16
# 1000미만의 자연수에서 3,5의 배수의 총합을 구하라.
result = 0
for n in range(1, 1000):
    if n % 3 == 0 or n % 5 == 0:
        result += n
# print(result)
# print(sum(list([x for x in range(1000) if x % 3 == 0 or x % 5 == 0])))

#17
# 게시판 페이징
# 입력 : 총건수(m), 한페이지에 보여줄 게시물수(n)
# 단 n은 1보다 크거나 같다. n >= 1
# 출력 : 총페이지수
def page(m, n):
    page = m // n #몫
    if m % n > 0 : #나머지가 0보다 클 때
        page += 1 #출력페이지 ++
    return(page)
# print(page(31, 10))

#18
# 숫자 배열하기
# 1에서 9까지의 숫자를 무작위로 배열하여 나온 배열 5개를 출력
def random() :
    import random
    return list[random.sample(list(range(1, 10)), 9)]
for i in range(5):
    print(random())

