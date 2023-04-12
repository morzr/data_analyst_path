**Question** ([link](https://py.checkio.org/en/mission/follow-instructions/))

You’ve received a letter from a friend whom you haven't seen or heard from for a while. In this letter he gives you instructions on how to find a hidden treasure!

In this mission you should follow a given list of instructions which will get you to a certain point on the map. A list of instructions is a string, each letter of this string points you in the direction of your next step.

The letter "f" - tells you to move forward, "b" - backward, "l" - left, and "r" - right.

It means that if the list of your instructions is "fflff" then you should move forward two times, make one step to the left and then again move two times forward.

Now, let's imagine that you are in the position (0, 0). If you move forward your position will change to (0, 1). If you move again it will be (0, 2). If your next step is to the left then your position will become (-1, 2). After the next two steps forward your coordinates will be (-1, 4).

Your goal is to find your final coordinates. Like in our case they are (-1, 4).

Input: A string.

Output: A tuple or list of two integers.

Examples:

```python
assert list(follow("fflff")) == [-1, 4]
assert list(follow("ffrff")) == [1, 4]
assert list(follow("fblr")) == [0, 0]
```


**My Solution**

```python
def follow(instructions: str) -> tuple[int, int] | list[int]:
    result_y = 0
    result_x = 0
    for letter in instructions:
        if letter == "f":
            result_y += 1
        elif letter == "l":
            result_x += -1
        elif letter == "r":
            result_x += 1
        elif letter == "b":
            result_y += -1
    return (result_x, result_y)


print("Example:")
print(list(follow("fflff")))

assert list(follow("fflff")) == [-1, 4]
assert list(follow("ffrff")) == [1, 4]
assert list(follow("fblr")) == [0, 0]

print("The mission is done! Click 'Check Solution' to earn rewards!")
```
