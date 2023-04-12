**Question ([link](https://py.checkio.org/en/mission/common-words/))**

Let's continue examining words. You are given two strings with words separated by commas. Try to find what is common between these strings. The words in the same string don't repeat.

Your function should find all of the words that appear in both strings. The result must be represented as a string of words separated by commas in alphabetic order.

Input: Two arguments as strings.

Output: The common words as a string.

Example:

```python
assert checkio("hello,world", "hello,earth") == "hello"
assert checkio("one,two,three", "four,five,six") == ""
assert checkio("one,two,three", "four,five,one,two,six,three") == "one,three,two"
```

**My Solution**

```python
def checkio(line1: str, line2: str) -> str:
    a = line1.split(",")
    b = line2.split(",")
    c = set(sorted(a))
    d = set(sorted(b))
    intersection = list(c.intersection(d))
    if len(intersection) == 0:
        result = ""
    else:
        result = sorted(intersection)
        result = ",".join(result)

    return result



print("Example:")
print(checkio("hello,world", "hello,earth"))
assert checkio("hello,world", "hello,earth") == "hello"
assert checkio("one,two,three", "four,five,six") == ""
assert checkio("one,two,three", "four,five,one,two,six,three") == "one,three,two"

print("The mission is done! Click 'Check Solution' to earn rewards!")
