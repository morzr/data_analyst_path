**Question ([link](https://py.checkio.org/en/mission/all-upper-ii/))**

Check if a given string has all symbols in upper case. If the string is empty or doesn't have any letter in it - function should return False.

Input: A string.

Output: A boolean.

Examples:

```python 
assert is_all_upper("ALL UPPER") == True
assert is_all_upper("all lower") == False
assert is_all_upper("mixed UPPER and lower") == False
assert is_all_upper("") == False
```

**My Solution**

```python
def is_all_upper(text:str) -> bool:
    if len(text) == 0:
        return False

    if text.isupper():
        return True
    else:
        return False

print("Example:")
print(is_all_upper("ALL UPPER"))

# These "asserts" are used for self-checking
assert is_all_upper("ALL UPPER") == True
assert is_all_upper("all lower") == False
assert is_all_upper("mixed UPPER and lower") == False
assert is_all_upper("") == False

print("The mission is done! Click 'Check Solution' to earn rewards!")
