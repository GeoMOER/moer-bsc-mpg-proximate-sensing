---
title: Writing code - programming
header:
  image: "/assets/images/title/header.png"
  caption: 'Photo by [Lukas Goumbik, from Pixabay](https://pixabay.com/de/users/goumbik-3752482/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=2055522){:target="_blank"}'
---
If you have never used python before, grab a coffee or tea, take an hour (or longer, if you work on the exercises) and check out this awesome introduction to python: 

[![Tutorial by Mosh](https://img.youtube.com/vi/kqtD5dpn9C8/0.jpg)](https://www.youtube.com/watch?v=kqtD5dpn9C8)


Here are some important bits:

## 1. The while Loop ##

The while loop in Python is used to execute a block of code repeatedly as long as a specified condition is true. Its syntax is as follows:

```python
while condition:
    # Code block to be executed while the condition is true
```

The condition is evaluated before each iteration of the loop. If the condition evaluates to True, the code block within the loop is executed. When the condition becomes False, the loop terminates, and the program continues with the next statement after the loop.

Example:
```python
count = 0
while count < 5:
    print("Count:", count)
    count += 1

```

Output:
```python
Count: 0
Count: 1
Count: 2
Count: 3
Count: 4

```
In this example, the while loop continues to execute as long as the count variable is less than 5. Once count reaches 5, the loop terminates.

## 2. The if Statement ##

The if statement is used to execute a block of code only if a specified condition is true. Its syntax is as follows:

```python
if condition:
    # Code block to be executed if the condition is true
```

The condition is evaluated, and if it is True, the code block following the if statement is executed. If the condition is False, the code block is skipped.

Example 
```python
x = 10
if x > 5:
    print("x is greater than 5")

```
Output:
```python
x is greater than 5
```

## 3. The else Statement ##

The else statement follows an if statement and is executed when the if condition is false. Its syntax is as follows:

```python
if condition:
    # Code block to be executed if the condition is true
else:
    # Code block to be executed if the condition is false

```
The else statement does not have a condition of its own. It is a catch-all for any condition that is not met by the preceding if statement.

Example:

```python
x = 2
if x > 5:
    print("x is greater than 5")
else:
    print("x is not greater than 5")

```

output:

```python
x is not greater than 5

```


## Practice I:
After connecting your sensor in unit 2 in the [simulator](https://wokwi.com/projects/new/micropython-pi-pico), write a python script so that it prints a message whenever the sensor gets activated.

## Practice II:
Generate a script which allows you to take time-lapse images via one of the base raspberry-pi cameras. Alternatively, try to time-schedule the 12V UV lamp from the practice chapter of unit02.