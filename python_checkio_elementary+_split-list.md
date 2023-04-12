**Question ([link](https://py.checkio.org/en/mission/split-list/))**


You have to split a given list into two lists inside an Iterable. If input sequence has an odd amount of elements, then the first list inside result Iterable should have more elements. If input sequence has no elements, then two empty lists inside result Iterable should be returned.

example

Input: A list.

Output: An Iterable of two lists.

Examples:

```python
assert list(split_list([1, 2, 3, 4, 5, 6])) == [[1, 2, 3], [4, 5, 6]]
assert list(split_list([1, 2, 3])) == [[1, 2], [3]]
assert list(split_list(["banana", "apple", "orange", "cherry", "watermelon"])) == [
    ["banana", "apple", "orange"],
    ["cherry", "watermelon"],
]
assert list(split_list([1])) == [[1], []]

```
**My Solution**

```python
def split_list(items: list) -> list:
    if len(items) == 0:
        return [[], []]
    
    if len(items) % 2 == 0:
        index_to_split = len(items)//2
    else:    
        index_to_split = len(items)//2 + 1 
        
    return [items[:index_to_split] , items[index_to_split:]] 
       
     
   


if __name__ == '__main__':
    print("Example:")
    print(split_list([1, 2, 3, 4, 5, 6]))

    # These "asserts" are used for self-checking and not for an auto-testing
    assert split_list([1, 2, 3, 4, 5, 6]) == [[1, 2, 3], [4, 5, 6]]
    assert split_list([1, 2, 3]) == [[1, 2], [3]]
    assert split_list([1, 2, 3, 4, 5]) == [[1, 2, 3], [4, 5]]
    assert split_list([1]) == [[1], []]
    assert split_list([]) == [[], []]
    print("Coding complete? Click 'Check' to earn cool rewards!")
