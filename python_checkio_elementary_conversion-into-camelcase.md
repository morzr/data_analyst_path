**Question** ([link](https://py.checkio.org/en/mission/conversion-into-camelcase/))

Your mission is to convert the name of a function (a string) from the Python format (for example "my_function_name") into CamelCase ("MyFunctionName"), where the first char of every word is in uppercase and all words are concatenated without any intervening characters.

Input: A function name as a string.

Output: The same string, but in CamelCase.

Example:

```python
assert to_camel_case("my_function_name") == "MyFunctionName"
assert to_camel_case("i_phone") == "IPhone"
```

**My Solution**

```python
def to_camel_case(name: str) -> str:
    splitted_name = name.split('_')
    camelcase = []
    for i in splitted_name:
        text = i.capitalize()
        camelcase.append(text)
    camelcase = ''.join(camelcase)
    print(camelcase)
    return camelcase



print("Example:")
print(to_camel_case("my_function_name"))

assert to_camel_case("my_function_name") == "MyFunctionName"
assert to_camel_case("i_phone") == "IPhone"

print("The mission is done! Click 'Check Solution' to earn rewards!")
