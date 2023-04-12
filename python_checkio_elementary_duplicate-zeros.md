**Question ([link](https://py.checkio.org/en/mission/duplicate-zeros/))**


"Sometimes, zeros resemble very tasty donut. And every time we finish a donut, we want another, and then another, and then another..."

You are given a list of integers. Your task in this mission is to duplicate (..., 🍩, ... --> ..., 🍩, 🍩, ...) all zeros (think about donuts ;-P) and return the result as any Iterable. Let's look on the example:

[1, 0, 2, 0] -> [1, 0, 0, 2, 0, 0]
    
Input: A list of integers.

Output: A list on another Iterable (tuple, generator, iterator) of integers.

Examples:

```python
assert list(duplicate_zeros([1, 0, 2, 3, 0, 4, 5, 0])) == [
    1,
    0,
    0,
    2,
    3,
    0,
    0,
    4,
    5,
    0,
    0,
]
assert list(duplicate_zeros([0, 0, 0, 0])) == [0, 0, 0, 0, 0, 0, 0, 0]
assert list(duplicate_zeros([100, 10, 0, 101, 1000])) == [100, 10, 0, 0, 101, 1000]
```

**My Solution**

```python
from typing import Iterable


def duplicate_zeros(donuts: list[int]) -> Iterable[int]:
    # your code herefinal_list = []
    final_list = [] 
    x = 0
    i = donuts[x]
    for i in donuts:
        if i!= 0:
            final_list.append(i)
        else:
            final_list.append(i)
            final_list.append(i)
    return final_list

    return []


print("Example:")
print(list(duplicate_zeros([1, 0, 2, 3, 0, 4, 5, 0])))

assert list(duplicate_zeros([1, 0, 2, 3, 0, 4, 5, 0])) == [
    1,
    0,
    0,
    2,
    3,
    0,
    0,
    4,
    5,
    0,
    0,
]
assert list(duplicate_zeros([0, 0, 0, 0])) == [0, 0, 0, 0, 0, 0, 0, 0]
assert list(duplicate_zeros([100, 10, 0, 101, 1000])) == [100, 10, 0, 0, 101, 1000]

print("The mission is done! Click 'Check Solution' to earn rewards!")
