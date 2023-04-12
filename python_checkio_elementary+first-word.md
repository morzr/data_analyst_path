**Question ([link](https://py.checkio.org/en/mission/first-word/))**

I might see a simplified version of this mission already First Word (simplified). This mission is a little bit more complex as not only English letters can be in the given string.

You are given a string where you have to find its first word.

When solving a task pay attention to the following points:

There can be dots and commas in a string.
A string can start with a letter or, for example, one/multiple dot(s) or space(s).
A word can contain an apostrophe and it's a part of a word.
The whole text can be represented with one word and that's it.
Input: A string.

Output: A string.

Example:

```python
assert first_word("Hello world") == "Hello"
assert first_word(" a word ") == "a"
assert first_word("don't touch it") == "don't"
assert first_word("greetings, friends") == "greetings"
```

**My Solution**

```python
def first_word(text: str) -> str:
    """
    function returns the first word in a given text.
    """
    only_words = list()
    
    for x in text:
        only_words = text.replace('.' , '  ').replace(',', ' ')
        only_words =  only_words.split()
    return only_words[0]


print("Example:")
print(first_word("Hello world"))

assert first_word("Hello world") == "Hello"
assert first_word(" a word ") == "a"
assert first_word("don't touch it") == "don't"
assert first_word("greetings, friends") == "greetings"
assert first_word("... and so on ...") == "and"
assert first_word("hi") == "hi"

print("The mission is done! Click 'Check Solution' to earn rewards!")
