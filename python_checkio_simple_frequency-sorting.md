**Question** ([link](https://py.checkio.org/en/mission/frequency-sorting/))

Sort the given list so that its elements should be grouped and those groups end up in the decreasing frequency order, that is, the number of times element appears in the list. If two elements have the same frequency, their groups should end up according to the natural order of elements. For example: [5, 2, 4, 1, 1, 1, 3] ==> [1, 1, 1, 2, 3, 4, 5].

If you want to practice more with the similar case, try Sort Array by Element Frequency mission.

Input: List of integers.

Output: List or another Iterable (tuple, iterator, generator).

Examples:

```python
assert list(frequency_sorting([1, 2, 3, 4, 5])) == [1, 2, 3, 4, 5]
assert list(frequency_sorting([3, 4, 11, 13, 11, 4, 4, 7, 3])) == [
    4,
    4,
    4,
    3,
    3,
    11,
    11,
    7,
    13,
]
```

**My Solution**
```python
from typing import List

def frequency_sorting(numbers: List[int]) -> List[int]:
    count = 0 
    counter_of_occurences = {}
    
    for x in numbers:
        frequency =  numbers.count(x)
        counter_of_occurences[x] = frequency
        
    sorted_items = sorted(counter_of_occurences.items(),key = lambda x:(x[1],-x[0]), reverse = True)
   
    items_by_frequency = [] 
    for x in sorted_items:
        items_by_frequency = items_by_frequency + [x[0]] * x[1] 
    return items_by_frequency
       
   
if __name__ == "__main__":
    print("Example:")
    print(frequency_sorting([1, 2, 3, 4, 5]))

    # These "asserts" using only for self-checking and not necessary for auto-testing
    #assert frequency_sorting([1, 2, 3, 4, 5]) == [1, 2, 3, 4, 5]
    assert frequency_sorting([3, 4, 11, 13, 11, 4, 4, 7, 3]) == [
        4,
        4,
        4,
        3,
        3,
        11,
        11,
        7,
        13,
    ]
    assert frequency_sorting([99, 99, 55, 55, 21, 21, 10, 10]) == [
        10,
        10,
        21,
        21,
        55,
        55,
        99,
        99,
    ], "Reversed"
    print("Coding complete? Click 'Check' to earn cool rewards!")
