**Question** ([link](https://py.checkio.org/en/mission/flatten-list/))

Nicola likes to categorize all sorts of things. He categorized a series of numbers and as the result of his efforts, a simple sequence of numbers became a deeply-nested list. Sophia and Stephan don't really understand his organization and need to figure out what it all means. They need your help to understand Nikolas crazy list.

There is a list which contains integers or other nested lists which may contain yet more lists and integers which then… you get the idea. You should put all of the integer values into one flat list. The order should be as it was in the original list with string representation from left to right.

We need to hide this program from Nikola by keeping it small and easy to hide. Because of this, your code should be shorter than 140 characters (with whitespaces).

Input: A nested list of integers.

Output: List or another Iterable (tuple, generator, iterator) of integers.

Examples:

```python
assert list(flat_list([1, 2, 3])) == [1, 2, 3]
assert list(flat_list([1, [2, 2, 2], 4])) == [1, 2, 2, 2, 4]
assert list(flat_list([[[2]], [4, [5, 6, [6], 6, 6, 6], 7]])) == [
    2,
    4,
    5,
    6,
    6,
    6,
    6,
    6,
    7,
]
assert list(flat_list([-1, [1, [-2], 1], -1])) == [-1, 1, -2, 1, -1]
```

**My Solution**
```python
def flat_list(array):


    # Final list to be returned
    result = []
 
    # Creating stack and adding
    # all elements into it
    stack = [array]
 
    # Iterate stack till it
    # does not get empty
    while stack:
 
        # Get the last element of the stack
        current = stack.pop(-1)
 
        # If the last element is a list,
        # add all the elements of that list in stack
        if isinstance(current, list):
            stack.extend(current)
             
        # Else add that element in the result
        else:
            result.append(current)
 
    # Reverse the result to get the
    # list in original order
    result.reverse()
 
    return result
 

    
    


if __name__ == '__main__':
    assert flat_list([1, 2, 3]) == [1, 2, 3], "First"
    assert flat_list([1, [2, 2, 2], 4]) == [1, 2, 2, 2, 4], "Second"
    assert flat_list([[[2]], [4, [5, 6, [6], 6, 6, 6], 7]]) == [2, 4, 5, 6, 6, 6, 6, 6, 7], "Third"
    assert flat_list([-1, [1, [-2], 1], -1]) == [-1, 1, -2, 1, -1], "Four"
    print('Done! Check it')

```
