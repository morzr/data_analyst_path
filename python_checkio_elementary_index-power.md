**Question** ([link](https://py.checkio.org/en/mission/index-power/))

You are given an array with positive numbers and a number N. You should find the N-th power of the element in the array with the index N. If N is outside of the array, then return -1. Don't forget that the first element has the index 0.

Let's look at a few examples:
- array = [1, 2, 3, 4] and N = 2, then the result is 32 == 9;
- array = [1, 2, 3] and N = 3, but N is outside of the array, so the result is -1.

Input: Two arguments. An array as a list of integers and a number as a integer.

Output: The result as an integer.

Example:

```python
assert index_power([1, 2, 3, 4], 2) == 9
assert index_power([1, 3, 10, 100], 3) == 1000000
assert index_power([0, 1], 0) == 1
assert index_power([1, 2], 3) == -1

```
**My Solution**
```python
def index_power(array: list, n: int) -> int:
    if n < len(array):
        return array[n] ** n 
    else:
        return -1
        
     

print('Example:')
print(index_power([1, 2, 3], 2))

assert index_power([1, 2, 3, 4], 2) == 9
assert index_power([1, 3, 10, 100], 3) == 1000000
assert index_power([0, 1], 0) == 1
assert index_power([1, 2], 3) == -1

print("The mission is done! Click 'Check Solution' to earn rewards!")
