**Question ([link](https://py.checkio.org/en/mission/easy-unpack/))**

Your mission here is to create a function that gets a tuple and returns a tuple with only 3 elements - the first, third and second element from the last for the given tuple.

![example](https://d17mnqrx9pmt3e.cloudfront.net/media/missions/media/1248ed1861f9458f80cb95b39e76d730/example.png)

*One important thing worth pointing out is that you need to use index in order to extract elements from the tuple. Pay attention, index counting starts from 0, not from 1. Which means that if you need to get the first element from the tuple **elements**, you should do **elements[0]**, and the second element is **elements[1]**.*
**Input:** A tuple, at least 3 elements long.
**Output:** A tuple.

**Examples:**

```python
assert easy_unpack((1, 2, 3, 4, 5, 6, 7, 9)) == (1, 3, 7)
assert easy_unpack((1, 1, 1, 1)) == (1, 1, 1)
assert easy_unpack((6, 3, 7)) == (6, 7, 3)
```


**Solution**

```python
def easy_unpack(elements: tuple) -> tuple:
    return (elements[0], elements[2], elements[-2])

print("Example:")
print(easy_unpack((1, 2, 3, 4, 5, 6, 7, 9)))

assert easy_unpack((1, 2, 3, 4, 5, 6, 7, 9)) == (1, 3, 7)
assert easy_unpack((1, 1, 1, 1)) == (1, 1, 1)
assert easy_unpack((6, 3, 7)) == (6, 7, 3)

print("The mission is done! Click 'Check Solution' to earn rewards!")
```
