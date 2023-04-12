**Question ([link](https://py.checkio.org/en/mission/backward-each-word/))**


In a given string you should reverse every word, but the words should stay in their places.

Input: A string.

Output: A string.

Example:

```python
assert backward_string_by_word("") == ""
assert backward_string_by_word("world") == "dlrow"
assert backward_string_by_word("hello world") == "olleh dlrow"
assert backward_string_by_word("hello   world") == "olleh   dlrow"
```

**My Solution**

```python
def backward_string_by_word(text: str) -> str:
    words = text.split(' ')
    reverse_words = []
    
    for word in words:
        reverse_words.append(word[::-1])
    
    backword_string = ' '.join(reverse_words)
    print(backword_string)
    return backword_string
    
   
print("Example:")
#print(backward_string_by_word(""))

#assert backward_string_by_word("") == ""
assert backward_string_by_word("world") == "dlrow"
assert backward_string_by_word("hello world") == "olleh dlrow"
assert backward_string_by_word("hello   world") == "olleh   dlrow"
assert backward_string_by_word("welcome to a game") == "emoclew ot a emag"

print("The mission is done! Click 'Check Solution' to earn rewards!")
