**Question** ([link](https://py.checkio.org/en/mission/majority/))

Ponts from solving the mission are also counted in this month's Leaderboard. At the bottom of the Leaderboard, you can find links to the other missions that count.
We have a list of booleans. Let's check if the majority of elements are True.

example

Some cases worth mentioning: 1) an empty list should return False; 2) if True-s and False-s have an equal amount, function should return False.

Input: A list of booleans.

Output: A Boolean.

Examples:

```python
assert is_majority([True, True, False, True, False]) == True
assert is_majority([True, True, False]) == True
assert is_majority([True, True, False, False]) == False
assert is_majority([True, True, False, False, False]) == False
```

**My Solution**
```python
def is_majority(items: list) -> bool:
    if items.count(True) > items.count(False):
        return True 
    else: 
        return False
                                     
    return items


if __name__ == '__main__':
    print("Example:")
    print(is_majority([True, True, False, True, False]))

    # These "asserts" are used for self-checking and not for an auto-testing
    assert is_majority([True, True, False, True, False]) == True
    assert is_majority([True, True, False]) == True
    assert is_majority([True, True, False, False]) == False
    assert is_majority([True, True, False, False, False]) == False
    assert is_majority([False]) == False
    assert is_majority([True]) == True
    assert is_majority([]) == False
    print("Coding complete? Click 'Check' to earn cool rewards!")
