**Question** ([link](https://py.checkio.org/en/mission/goes-after/))

In a given word you need to check if one symbol goes only right after another.

Cases you should expect while solving this challenge:

one of the symbols is not in the given word - your function should return False;
any symbol appears in a word more than once - use only the first one;
two symbols are the same - your function should return False;
the condition is case sensitive, which means 'a' and 'A' are two different symbols.
Input: Three arguments. The first one is a given string, second is a symbol that should go first, and the third is a symbol that should go after the first one.

Output: A bool.

Examples:

```python
assert goes_after("world", "w", "o") == True
assert goes_after("world", "w", "r") == False
assert goes_after("world", "l", "o") == False
assert goes_after("panorama", "a", "n") == True

```
**My Solution**

```python
def goes_after(word: str, first: str, second: str) -> bool:
    if first in word and second in word and first != second and word.index(second) - word.index(first) == 1:
        return True
    else:
        return False
    


print("Example:")
print(goes_after("world", "w", "o"))

assert goes_after("world", "w", "o") == True
assert goes_after("world", "w", "r") == False
assert goes_after("world", "l", "o") == False
assert goes_after("panorama", "a", "n") == True
assert goes_after("list", "l", "o") == False
assert goes_after("", "l", "o") == False
assert goes_after("list", "l", "l") == False
assert goes_after("world", "d", "w") == False

print("The mission is done! Click 'Check Solution' to earn rewards!")
