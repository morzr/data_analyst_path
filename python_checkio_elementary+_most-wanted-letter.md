**Question ([link](https://py.checkio.org/en/mission/most-wanted-letter/))**

We have prepared a set of Editor's Choice Solutions. You will see them first after you solve the mission. In order to see all other solutions you should change the filter.

You are given a text, which contains different English letters and punctuation symbols. You should find the most frequent letter in the text. The letter returned must be in lower case.
While checking for the most wanted letter, casing does not matter, so for the purpose of your search, "A" == "a". Make sure you do not count punctuation symbols, digits and whitespaces, only letters.

If you have two or more letters with the same frequency, then return the letter which comes first in the Latin alphabet. For example -- "one" contains "o", "n", "e" only once for each, thus we choose "e".

Input: A text for analysis as a string.

Output: The most frequent letter in lower case as a string.

Example:

```python
assert checkio("Hello World!") == "l"
assert checkio("How do you do?") == "o"
assert checkio("One") == "e"
assert checkio("Oops!") == "o"
```

**My Solution**

```python
def checkio(text: str) -> str:
    num_times = { }
    lower_text = text.lower()
    num_times = {letter:lower_text.count(letter) for letter in set(lower_text) if letter.isalpha()}
    freq = max(num_times.values())
    let = min(k for k, v in num_times.items() if v == freq)
    print(let)
    return let
    return ""


print("Example:")
print(checkio("Hello World!"))

assert checkio("Hello World!") == "l"
assert checkio("How do you do?") == "o"
assert checkio("One") == "e"
assert checkio("Oops!") == "o"
assert checkio("AAaooo!!!!") == "a"
assert checkio("abe") == "a"

print("The mission is done! Click 'Check Solution' to earn rewards!")
