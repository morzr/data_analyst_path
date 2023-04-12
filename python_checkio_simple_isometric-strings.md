**Question ([link](https://py.checkio.org/en/mission/isometric-strings/))**

Maybe it's a cipher? Maybe, but we don’t know for sure.

Maybe you can call it "homomorphism"? I wish I knew this word before.

You need to check that the String A is isometric to the String B. There exists a function that turns characters from String A into characters in the same spot in String B.

Characters in String A correspond to a unique character value in String B. Characters in String B are allowed to correspond to multiple character values in String A.


Input: Two arguments. String A and String B.

Output: Boolean.

Examples:

```python
assert isometric_strings("add", "egg") == True
assert isometric_strings("foo", "bar") == False
assert isometric_strings("bar", "foo") == True
assert isometric_strings("", "") == True
```

**My Solution**

```python
def isometric_strings(a: str, b: str) -> bool:
    dic = {}
    for ind, char in enumerate(a):
        dic[char] = dic.get(char, set()).union(set(b[ind]))
        if len(dic[char]) > 1:
            return False
     
        
    return True 


print("Example:")
print(isometric_strings("add", "egg"))

assert isometric_strings("add", "egg") == True
assert isometric_strings("foo", "bar") == False
assert isometric_strings("bar", "foo") == True
assert isometric_strings("", "") == True
assert isometric_strings("all", "all") == True
assert isometric_strings("gogopy", "doodle") == False
assert isometric_strings("abba", "cccc") == True

print("The mission is done! Click 'Check Solution' to earn rewards!")
