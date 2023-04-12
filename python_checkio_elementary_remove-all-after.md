**Question** ([link](https://py.checkio.org/en/mission/remove-all-after/))

Not all of the elements are important. What you need to do here is to remove all of the elements after the given one from list.

example

For illustration, we have a list [1, 2, 3, 4, 5] and we need to remove all the elements that go after 3 - which is 4 and 5.

We have two edge cases here:

if a cutting element cannot be found, then the list shouldn't be changed;
if the list is empty, then it should remains empty.
Input: List of integers and the border element integer.

Output: List or other Iterable (tuple, iterator, generator ...) of integers.

Examples:

```python
assert list(remove_all_after([1, 2, 3, 4, 5], 3)) == [1, 2, 3]
assert list(remove_all_after([1, 1, 2, 2, 3, 3], 2)) == [1, 1, 2]
assert list(remove_all_after([1, 1, 2, 4, 2, 3, 4], 2)) == [1, 1, 2]
assert list(remove_all_after([1, 1, 5, 6, 7], 2)) == [1, 1, 5, 6, 7]
```

**My Solution**
```python
from typing import Iterable


def remove_all_after(items: list, border: int) -> Iterable:
   
    if len(items) == 0: 
        return items 
    if not border in items:
        return items
   
    return items[:items.index(border)+1]
   
    


if __name__ == '__main__':
    print("Example:")
    print(list(remove_all_after([1, 2, 3, 4, 5], 3)))

    # These "asserts" are used for self-checking and not for an auto-testing
    assert list(remove_all_after([1, 2, 3, 4, 5], 3)) == [1, 2, 3]
    assert list(remove_all_after([1, 1, 2, 2, 3, 3], 2)) == [1, 1, 2]
    assert list(remove_all_after([1, 1, 2, 4, 2, 3, 4], 2)) == [1, 1, 2]
    assert list(remove_all_after([1, 1, 5, 6, 7], 2)) == [1, 1, 5, 6, 7]
    assert list(remove_all_after([], 0)) == []
    assert list(remove_all_after([7, 7, 7, 7, 7, 7, 7, 7, 7], 7)) == [7]
    print("Coding complete? Click 'Check' to earn cool rewards!")
