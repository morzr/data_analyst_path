**Question ([link](https://py.checkio.org/en/mission/secret-message/))**

"Where does a wise man hide a leaf? In the forest. But what does he do if there is no forest? ... He grows a forest to hide it in."
-- Gilbert Keith Chesterton

Ever tried to send a secret message to someone without using the postal service? You could use newspapers to tell your secret. Even if someone finds your message, it's easy to brush them off as paranoid and as a conspiracy theorist. One of the simplest ways to hide a secret message is to use capital letters. Let's find some of these secret messages.

You are given a chunk of text. Gather all capital letters in one word in the order that they appear in the text.

For example: text = " H ow are you? E h, ok. L ow or L ower? O hhh.", if we collect all of the capital letters, we get the message "HELLO".

Input: A text as a string (unicode).

Output: The secret message as a string or an empty string.

Example:

```python
find_message(('How are you? Eh, ok. Low or Lower? '
 'Ohhh.')) == 'HELLO'
find_message('hello world!') == ''
find_message('HELLO WORLD!!!') == 'HELLOWORLD'
```


**My Solution**

```python
def find_message(message: str) -> str:
    upper_letters = []

    for letter in message:
        if letter.isupper():
            upper_letters.append(letter)

    return ''.join(upper_letters)




if __name__ == '__main__':
    print("Example:")
    print(find_message(('How are you? Eh, ok. Low or Lower? '
                        + 'Ohhh.')))

    # These "asserts" are used for self-checking and not for an auto-testing
    assert find_message(('How are you? Eh, ok. Low or Lower? '
                         + 'Ohhh.')) == 'HELLO'
    assert find_message('hello world!') == ''
    assert find_message('HELLO WORLD!!!') == 'HELLOWORLD'
    print("Coding complete? Click 'Check' to earn cool rewards!")
