**Question** ([link](https://py.checkio.org/en/mission/median/))

We have prepared a set of Editor's Choice Solutions. You will see them first after you solve the mission. In order to see all other solutions you should change the filter.
elki
A median is a numerical value separating the upper half of a sorted list of numbers from the lower half. In a list where there are an odd number of entities, the median is the number found in the middle of the list. If the list contains an even number of entities, then there is no single middle value, instead the median becomes the average of the two numbers found in the middle. For this mission, you are given a non-empty list of natural integers. With it, you must separate the upper half of the numbers from the lower half and find the median.

If you want to practice more with the similar case, try Middle Characters mission.

Input: A list of integers.

Output: The median as a float or an integer.

Examples:

```python
assert checkio([1, 2, 3, 4, 5]) == 3
assert checkio([3, 1, 2, 5, 3]) == 3
assert checkio([1, 300, 2, 200, 1]) == 2
assert checkio([3, 6, 20, 99, 10, 15]) == 12.5
```

**My Solution**

```python
from typing import List
import statistics

def checkio(data: List[int]) -> [int, float]:

    sorted_data_list = list(sorted(data))
    data_lenght = len(sorted_data_list)
    if len(data) % 2 != 0: 
        median = sorted_data_list[int((data_lenght)/2)] 
    else:
        median = (sorted_data_list[int(data_lenght/2)-1] + sorted_data_list[int(data_lenght/2)]) /2 
    print (median)
    return median 
    
#These "asserts" using only for self-checking and not necessary for auto-testing
if __name__ == '__main__':
    print("Example:")
    print(checkio([1, 2, 3, 4, 5]))

    assert checkio([1, 2, 3, 4, 5]) == 3
    #assert checkio([3, 1, 2, 5, 3]) == 3
    assert checkio([1, 300, 2, 200, 1]) == 2
    assert checkio([3, 6, 20, 99, 10, 15]) == 12.5
    print("Start the long test")
    assert checkio(list(range(1000000))) == 499999.5
    print("Coding complete? Click 'Check' to earn cool rewards!")
