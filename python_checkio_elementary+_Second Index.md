**Question ([link](https://py.checkio.org/en/mission/second-index/))**

You are given two strings and you have to find an index of the second occurrence of the second string in the first one.

Let's go through the first example where you need to find the second occurrence of "s" in a word "sims". It’s easy to find its first occurrence with a function index or find which will point out that "s" is the first symbol in a word "sims" and therefore the index of the first occurrence is 0. But we have to find the second "s" which is 4th in a row and that means that the index of the second occurrence (and the answer to a question) is 3.

Input: Two strings.

Output: Int or None

Example:
```python
assert second_index("sims", "s") == 3
assert second_index("find the river", "e") == 12
assert second_index("hi", " ") == None
assert second_index("hi mayor", " ") == None

```
**My Solution**

```python
def second_index(text: str, symbol: str) -> [int, None]:
    """
    returns the second index of a symbol in a given text
    """
    if text.count(symbol) < 2: 
        return None 
    first_occurance = text.find(symbol)
    return text.find(symbol,first_occurance + 1)
   


print("Example:")
print(second_index("sims", "s"))

assert second_index("sims", "s") == 3
assert second_index("find the river", "e") == 12
assert second_index("hi", " ") == None
assert second_index("hi mayor", " ") == None
assert second_index("hi mr Mayor", " ") == 5

print("The mission is done! Click 'Check Solution' to earn rewards!")
