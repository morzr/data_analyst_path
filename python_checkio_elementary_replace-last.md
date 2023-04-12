**Question** ([link](https://py.checkio.org/en/mission/replace-last/))

In a given list the last element should become the first one. An empty list or list with only one element should stay the same

example

Input: List.

Output: Iterable (tuple, generator, Iterator ...).

Example:

```python
assert list(replace_last([2, 3, 4, 1])) == [1, 2, 3, 4]
assert list(replace_last([1, 2, 3, 4])) == [4, 1, 2, 3]
assert list(replace_last([1])) == [1]
assert list(replace_last([])) == []

```

**My Solution**
```python
from typing import Iterable


def replace_last(line: list) -> Iterable:
    if len(line) <= 1:
        return line
    line.insert(0,line.pop(-1))
    return line 
    
        
print("Example:")
print(list(replace_last([2, 3, 4, 1])))

assert list(replace_last([2, 3, 4, 1])) == [1, 2, 3, 4]
assert list(replace_last([1, 2, 3, 4])) == [4, 1, 2, 3]
assert list(replace_last([1])) == [1]
assert list(replace_last([])) == []

print("The mission is done! Click 'Check Solution' to earn rewards!")
