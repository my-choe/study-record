# 🍎 Python 예제 🍎

```python
#19 
# 리스트 역순으로 가져오기
def for_each_right(itr, fn) :
    for el in itr[::-1] :
        fn(el)
# for_each_right([1, 2, 3], print) # 3 2 1

#20
#중복된 값 있는지 확인
def has_duplicates(lst) :
    return len(lst) != len(set(lst))
x = [1, 2, 3, 4, 5, 5, 6]
y = [1, 2, 3, 4, 5]
# has_duplicates(x) #True
# has_duplicates(y) #False

#21
#리스트의 첫번째 값 가져오기
def head(lst) :
    return lst[0]
# head([1, 2, 3]) # 1

#22
# start와 end 사이의 범위 구하기
def in_range(n, start, end = 0):
    return start <= n <= end if end >= start else end <= n <= start   
# print(in_range(3, 2, 5)) #True
# print(in_range(3, 4)) #True
# print(in_range(2, 3, 5)) #False
# print(in_range(3, 2)) #False

#23
# 리스트의 모든 값 반환
def initial(lst) :
    return lst[0:-1] #뒤에서 첫번째 값이 -1
# print(initial([1, 2, 3])) #[1,2]

#24
# 주어진 범위만큼의 리스트를 만듦
def initialize_list_with_range(end, start = 0, step = 1) :
    return list(range(start, end + 1, step))
# print(initialize_list_with_range(5)) # [0, 1, 2, 3, 4, 5]
# print(initialize_list_with_range(7, 3)) # [3, 4, 5, 6, 7]
# print(initialize_list_with_range(9, 0, 2)) # [0, 2, 4, 6, 8]

#25
# 주어진 값으로 채워진 리스트 만듦
def initialize_list_with_values(n, val = 0):
    return [val for x in range(n)]
# print(initialize_list_with_values(5, 2)) #[2, 2, 2, 2, 2]

#26
# 두 리스트에 모두 존재하는 값 반환
def intersection(a, b) :
    _a, _b = set(a), set(b)
    return list(_a & _b)
# print(intersection([1, 2, 3], [4, 3, 2])) # [2, 3]

#27
# 첫번째 숫자가 두번째 숫자로 나눠떨어지는지 판별
def is_divisible(dividend, divisor) :
    return dividend % divisor == 0
# print(is_divisible(6, 3)) #True

#28
# 주어진 숫자가 짝수일 경우 true
def is_even(num) :
    return num % 2 == 0
# print(is_even(3)) #False

#29
# 주어진 숫자가 홀수일 경우 true/false
def is_odd(num) :
    return num % 2 != 0
# print(is_odd(3)) #True

#30
# dictionary의 모든 키를 list로 변환
def keys_only(flat_dict):
    return list(flat_dict.keys())
ages = {
    "Peter" : 10,
    "Isabel" : 11,
    "Anna" : 9,
}
# print(keys_only(ages)) # ['Peter', 'Isabel', 'Anna']

#31
# 리스트의 마지막 값 갖고오기
def last(lst) : 
    return lst[-1]
# print(last([1, 2, 3])) # 3

#32
# 주어진 함수를 리스트의 각 값에 적용 후 최대값 반환
def max_by(lst, fn) :
    return max(map(fn, lst))
# print(max_by([{'n' : 4}, {'n':2}, {'n':8}, {'n':6}], lambda v : v['n'])) #8

#33
# 리스트에서 가장 큰 값의 인덱스 반환
def max_element_index(arr):
    return arr.index(max(arr))
# print(max_element_index([5, 8, 9, 7, 10, 3, 0])) #4

#34
# 리스트에서 큰 순서대로 n개의 값 반환
def max_n(lst, n=1):
    return sorted(lst, reverse = True)[:n] #sorted는 기본 오름차순 reverse True하면 내림차순
# print(max_n([1, 2, 3])) #[3]
# print(max_n([1, 2, 3], 2)) #[3, 2]

#35
# 리스트의 중앙값 반환
def median(list):
    list.sort()
    list_length = len(list)
    if list_length % 2 == 0 :
        return (list[int(list_length / 2) - 1] + list[int(list_length / 2)]) / 2
    return list[int(list_length / 2)]

# print(median([1, 2, 3])) # 2
# print(median([1, 2, 3, 4])) # 2.5

#36
# 최소값 반환
def min_by(lst, fn):
    return min(map(fn, lst))
# print(min_by([{'n' : 4}, {'n':2}, {'n':8}, {'n':6}], lambda v : v['n'])) #2

#37
# 리스트에서 작은 순서대로 n개의 값 반환
def min_n(lst, n = 1) :
    return sorted(lst, reverse=False)[:n]
# print(min_n([1, 2, 3])) #[1]
# print(min_n([1, 2, 3], 2)) #[1, 2]

#38
# 리스트에서 가장 갯수가 많은 값 반환
def most_frequent(list):
    return max(set(list), key=list.count)
# print(most_frequent([1, 2, 1, 2, 3, 2, 1, 4, 2])) #2

#39
# 주어진 횟수만큼 동일한 문자열 출력
def n_times_string(s, n):
    return (s * n)
# print(n_times_string('python', 4)) #pythonpythonpythonpython

#40
#주어진 갯수의 값을 리스트의 끝으로 이동
def offset(lst, offset):
    return lst[offset:] + lst[:offset]
print(offset([1, 2, 3, 4, 5], 2)) #[3, 4, 5, 1, 2]
print(offset([1, 2, 3, 4, 5], -2)) #[4, 5, 1, 2, 3]
```
