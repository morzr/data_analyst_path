**Question** ([link](https://py.checkio.org/en/mission/time-converter-12h-to-24h/))

You are the modern man who prefers the 24-hour time format. But the 12-hour format is used in some places. Your task is to convert the time from the 12-h format into 24-h by following the next rules:
- the output format should be 'hh:mm'
- if the output hour is less than 10 - write '0' before it. For example: '09:05'
Here you can find some useful information about the 12-hour format .

example

Input: Time in a 12-hour format (as a string).

Output: Time in a 24-hour format (as a string).

Example:

```python
time_converter('12:30 p.m.') == '12:30'
time_converter('9:00 a.m.') == '09:00'
time_converter('11:15 p.m.') == '23:15'
```

**My Solution**
```python
def time_converter(time):
    hours_and_minutes, am_pm = time.split(' ')
    hours_str, minutes_str = hours_and_minutes.split(':')
    
    hours = int(hours_str)
    minutes = int(minutes_str)
    
    is_am = am_pm == 'a.m.'
    if hours == 12:
        if is_am:
            hours = 0
    elif not is_am:
        hours += 12
        
    return '{}:{}'.format(str(hours).zfill(2), str(minutes).zfill(2))

"""from datetime import datetime
def time_converter(time):
    #replace this for solution
    if time[-4:] == "a.m." and time[:2] == "12":
        return "00" + time[2:-5] 
    elif time[-4:] == "a.m.":
        return time[:-5] 
    elif time[-4:] == "p.m." and time[:2] == "12": 
        return time[:-5]
    else:
        return str(int(time[:2]) +12) + time[2:5]
    print(time)
    return time"""

if __name__ == '__main__':
    print("Example:")
    print(time_converter('12:30 p.m.'))

    #These "asserts" using only for self-checking and not necessary for auto-testing
    assert time_converter('12:30 p.m.') == '12:30'
    print(time_converter('9:00 a.m.'))
    assert time_converter('9:00 a.m.') == '09:00'
    assert time_converter('11:15 p.m.') == '23:15'
    print("Coding complete? Click 'Check' to earn cool rewards!")
