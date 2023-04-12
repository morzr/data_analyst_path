**Question ([link](https://py.checkio.org/en/mission/all-the-same/))**
In this mission you should check if all elements in the given list are equal.

Input: List.

Output: Bool.

Example:

```python
assert all_the_same([1, 1, 1]) == True
assert all_the_same([1, 2, 1]) == False
assert all_the_same([1, "a", 1]) == False
assert all_the_same([1, 1, 1, 2]) == False
```
**My Solution**

```python
from typing import List, Any
def all_the_same(elements: List[Any]) -> bool:
    
    if len(elements) == 0:
        return True 
    if elements.count(elements[0]) == len(elements):
        return True 
    
    return False
   
print("Example:")
print(all_the_same([1, 1, 1]))

assert all_the_same([1, 1, 1]) == True
assert all_the_same([1, 2, 1]) == False
assert all_the_same([1, 1, 1, 2]) == False
assert all_the_same([2, 1, 1, 1]) == False
assert all_the_same([]) == True
assert all_the_same([1]) == True

print("The mission is done! Click 'Check Solution' to earn rewards!")
```
