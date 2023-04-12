**Question ([link](https://py.checkio.org/en/mission/digits-multiplication/))**

We have prepared a set of Editor's Choice Solutions. You will see them first after you solve the mission. In order to see all other solutions you should change the filter.
juggler
You are given a positive integer. Your function should calculate the product of the digits excluding any zeroes.

For example: The number given is 123405. The result will be 1*2*3*4*5=120 (don't forget to exclude zeroes).

Input: A positive integer.

Output: The product of the digits as an integer.

Examples:

```python
assert checkio(123405) == 120
assert checkio(999) == 729
assert checkio(1000) == 1
assert checkio(1111) == 1
```

**My Solution**

```python
def checkio(number: int) -> int:
    multiple_number = []
    text = str(number)
    for i in text:
        if i != '0' :
            multiple_number.append(int(i))
    multiplier = 1
    for number in multiple_number:
        multiplier = multiplier * number
    return multiplier


    

print("Example:")
print(checkio(123405))

assert checkio(123405) == 120
assert checkio(999) == 729
assert checkio(1000) == 1
assert checkio(1111) == 1

print("The mission is done! Click 'Check Solution' to earn rewards!")
