**Question** ([link](https://py.checkio.org/en/mission/compress-list/))

A given list should be "compressed" in a way so, instead of two (or more) equal elements, staying one after another, there should be only one in the result Iterable (list, tuple, iterator, generator).

example

Input: A list.

Output: "Compressed" List or another Iterable (tuple, iterator, generator).

Examples:

```python
assert list(compress([5, 5, 5, 4, 5, 6, 6, 5, 5, 7, 8, 0, 0])) == [
    5,
    4,
    5,
    6,
    5,
    7,
    8,
    0,
]
assert list(compress([1, 1, 1, 1, 2, 2, 2, 1, 1, 1])) == [1, 2, 1]
assert list(compress([7, 7])) == [7]
assert list(compress([])) == []
```


**My Solution**
```python
from typing import Iterable


def compress(items: list) -> Iterable:
    current_compress = []
    
    for i in range(len(items)):
        if i + 1 < len(items) and items[i] == items[i + 1]:
            continue 
             
        else:
            current_compress.append(items[i]) 
            
    print(current_compress)
    return current_compress


if __name__ == '__main__':
    #print("Example:")
    print(list(compress([
  5, 5, 5,
  4, 5, 6,
  6, 5, 5,
  7, 8, 0,
  0])))

    # These "asserts" are used for self-checking and not for an auto-testing
    assert list(compress([
  5, 5, 5,
  4, 5, 6,
  6, 5, 5,
  7, 8, 0,
  0])) == [5, 4, 5, 6, 5, 7, 8, 0]
    assert list(compress([1, 1, 1, 1, 2, 2, 2, 1, 1, 1])) == [1, 2, 1]
    assert list(compress([7, 7])) == [7]
    assert list(compress([])) == []
    assert list(compress([1, 2, 3, 4])) == [1, 2, 3, 4]
    assert list(compress([9, 9, 9, 9, 9, 9, 9])) == [9]
    print("Coding complete? Click 'Check' to earn cool rewards!")
