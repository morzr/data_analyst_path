**Question ([link](https://py.checkio.org/en/mission/date-and-time-converter/))**

Computer date and time format consists only of numbers, for example: 21.05.2018 16:30.
Humans prefer to see something like this: 21 May 2018 year, 16 hours 30 minutes.
Your task is simple - convert the input date and time from computer format into a "human" format.

example

Input: Date and time as a string

Output: The same date and time, but in a more readable format as a string

Example:

```python
assert date_time("01.01.2000 00:00") == "1 January 2000 year 0 hours 0 minutes"
assert date_time("09.05.1945 06:07") == "9 May 1945 year 6 hours 7 minutes"
```

**My Solution**

```python
from datetime import datetime
def date_time(time: str) -> str:
    # replace this for solution
    # "%d %b %Y %H %M"
    converted_time= datetime.strptime( time, "%d.%m.%Y %H:%M")
    formatted_time = converted_time.strftime("%-d %B %Y year %-H hours %-M minutes")
    formatted_time = formatted_time.replace("1 minutes", "1 minute")
    formatted_time = formatted_time.replace("1 hours", "1 hour")
    
    print(formatted_time)
    return formatted_time

if __name__ == "__main__":
    print("Example:")
    print(date_time("01.01.2000 00:00"))

    # These "asserts" using only for self-checking and not necessary for auto-testing
    assert (
        date_time("01.01.2000 00:00") == "1 January 2000 year 0 hours 0 minutes"
    ), "Millenium"
    assert (
        date_time("09.05.1945 06:30") == "9 May 1945 year 6 hours 30 minutes"
    ), "Victory"
    assert (
        date_time("20.11.1990 03:55") == "20 November 1990 year 3 hours 55 minutes"
    ), "Somebody was born"
    print("Coding complete? Click 'Check' to earn cool rewards!")
