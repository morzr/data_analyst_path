**Question** ([link](https://py.checkio.org/en/mission/flatten-dict/))

Nikola likes to categorize everything in sight. One time Stephan gave him a label maker for his birthday, and the robots were peeling labels off of every surface in the ship for weeks. He has since categorized all the reagents in his laboratory, books in the library and notes on the desk. But then he learned about Python dictionaries, and categorized all the possible configurations for Sophia’s drones. Now the files are organized in a deep nested structure, but Sophia doesn’t like this. Let's help Sophia to flatten these dictionaries.

Python dictionaries are a convenient data type to store and process configurations. They allow you to store data by keys to create nested structures. You are given a dictionary where the keys are strings and the values are strings or dictionaries. The goal is flatten the dictionary, but save the structures in the keys. The result should be the a dictionary without the nested dictionaries. The keys should contain paths that contain the parent keys from the original dictionary. The keys in the path are separated by a "/". If a value is an empty dictionary, then it should be replaced by an empty string (""). Let's look at an example:

```python
{
    "name": {
        "first": "One",
        "last": "Drone"
    },
    "job": "scout",
    "recent": {},
    "additional": {
        "place": {
            "zone": "1",
            "cell": "2"}
    }
}
The result will be:

{"name/first": "One",           # one parent
 "name/last": "Drone",
 "job": "scout",                # root key
 "recent": "",                  # empty dict
 "additional/place/zone": "1",  # third level
 "additional/place/cell": "2"}
```

**My Solution**
```python
def flatten(dictionary):
    result = {}
    stack = [dictionary]
    
    while stack:
        current = stack.pop(-1)

        for outer_key, outer_value in current.items():
            if outer_value == {}:
                outer_value = ""

            if isinstance(outer_value, dict):
                dict_with_path_keys = {}

                for inner_key, inner_value in outer_value.items():
                    dict_with_path_keys[outer_key + "/" + inner_key] = inner_value

                stack.append(dict_with_path_keys)
            else:
                result[outer_key] = outer_value

    print(result)
    return result

if __name__ == '__main__':
    test_input = {"key": {"deeper": {"more": {"enough": "value"}}}}
    print(' Input: {}'.format(test_input))
    print('Output: {}'.format(flatten(test_input)))

    #These "asserts" using only for self-checking and not necessary for auto-testing
    assert flatten({"key": "value"}) == {"key": "value"}, "Simple"
    assert flatten(
        {"key": {"deeper": {"more": {"enough": "value"}}}}
    ) == {"key/deeper/more/enough": "value"}, "Nested"
    assert flatten({"empty": {}}) == {"empty": ""}, "Empty value"
    assert flatten({"name": {
                        "first": "One",
                        "last": "Drone"},
                    "job": "scout",
                    "recent": {},
                    "additional": {
                        "place": {
                            "zone": "1",
                            "cell": "2"}}}
    ) == {"name/first": "One",
          "name/last": "Drone",
          "job": "scout",
          "recent": "",
          "additional/place/zone": "1",
          "additional/place/cell": "2"}
    print('You all set. Click "Check" now!')
