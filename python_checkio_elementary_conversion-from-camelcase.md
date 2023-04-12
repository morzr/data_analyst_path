**Question** ([link](https://py.checkio.org/en/mission/conversion-from-camelcase/))

Your mission is to convert the name of a function (a string) from CamelCase ("MyFunctionName") into the Python format ("my_function_name") where all chars are in lowercase and all words are concatenated with an intervening underscore symbol "_".

Input: A function name as a CamelCase string.

Output: The same string, but in under_score.

Example:

```python
assert from_camel_case("MyFunctionName") == "my_function_name"
assert from_camel_case("IPhone") == "i_phone"
```

**My Solution**

```python
def from_camel_case(name: str) -> str:
    words = []
    for letter in name:
        if letter.isupper():
            words.append( letter.lower())
        else:
            words[-1] += letter

    print('_'. join(words))
    return '_'. join(words)
    


print("Example:")
print(from_camel_case("MyFunctionName"))

assert from_camel_case("MyFunctionName") == "my_function_name"
assert from_camel_case("IPhone") == "i_phone"

print("The mission is done! Click 'Check Solution' to earn rewards!")
