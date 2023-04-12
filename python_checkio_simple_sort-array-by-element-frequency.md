**Question ([link](https://py.checkio.org/en/mission/sort-array-by-element-frequency/))**


Sort the given list so that its elements should be grouped and those groups end up in the decreasing frequency order, that is, the number of times element appears in list. If two elements have the same frequency, their groups should end up in the same order as the first appearance of element in the list.

If you want to practice more with the similar case, try Frequency Sorting mission.

Input: List

Output: List or another Iterable (tuple, iterator, generator)

Examples:

```python
assert list(frequency_sort([4, 6, 2, 2, 6, 4, 4, 4])) == [4, 4, 4, 4, 6, 6, 2, 2]
assert list(frequency_sort([4, 6, 2, 2, 2, 6, 4, 4, 4])) == [4, 4, 4, 4, 2, 2, 2, 6, 6]
assert list(frequency_sort(["bob", "bob", "carl", "alex", "bob"])) == [
    "bob",
    "bob",
    "bob",
    "carl",
    "alex",
]
assert list(frequency_sort([17, 99, 42])) == [17, 99, 42]
```

**My Solution**

```python
def frequency_sort(items):
    count = 0 
    
    counter_of_occurences = {} 
    for x in items: 
        frequences = items.count(x) 
        counter_of_occurences[x] = frequences
    
    sorted_items = sorted(counter_of_occurences.items(), key = lambda x:x[1], reverse = True)
    items_by_frequency = [] 
    for x in sorted_items:
        items_by_frequency = items_by_frequency + [x[0]] * x[1]
    print(items_by_frequency)   
    return items_by_frequency

if __name__ == '__main__':
    print("Example:")
    print(frequency_sort([4, 6, 2, 2, 6, 4, 4, 4]))

    # These "asserts" are used for self-checking and not for an auto-testing
    assert list(frequency_sort([4, 6, 2, 2, 6, 4, 4, 4])) == [4, 4, 4, 4, 6, 6, 2, 2]
    assert list(frequency_sort(['bob', 'bob', 'carl', 'alex', 'bob'])) == ['bob', 'bob', 'bob', 'carl', 'alex']
    assert list(frequency_sort([17, 99, 42])) == [17, 99, 42]
    assert list(frequency_sort([])) == []
    assert list(frequency_sort([1])) == [1]
    print("Coding complete? Click 'Check' to earn cool rewards!")
