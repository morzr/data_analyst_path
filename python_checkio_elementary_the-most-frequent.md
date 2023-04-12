**Question ([link](https://py.checkio.org/en/mission/the-most-frequent/))**

You have a sequence of strings, and you’d like to determine the most frequently occurring string in the sequence. It can be only one.

Input: non empty list of strings.

Output: a string.

Example:

```python
assert most_frequent(["a", "b", "c", "a", "b", "a"]) == "a"
assert most_frequent(["a", "a", "bi", "bi", "bi"]) == "bi"
```
**My Solution**

```python
def most_frequent(data: list[str]) -> str:
     return max(data, key=data.count)

print("Example:")
print(most_frequent(["a", "b", "c", "a", "b", "a"]))

assert most_frequent(["a", "b", "c", "a", "b", "a"]) == "a"
assert most_frequent(["a", "a", "bi", "bi", "bi"]) == "bi"

print("The mission is done! Click 'Check Solution' to earn rewards!")
