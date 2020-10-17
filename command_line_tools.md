# Command Line Tools

## f-strings

Decimal Formatting
Formatting decimal or floating point numbers with f-strings is easy - you can pass in both a field width and a precision. The format is {value:width.precision}. Let’s format pi (3.1415926) to two decimal places - we’ll set the width to 1 because we don’t need padding, and the precision to 3, giving us the one number to the left of the decimal and the two numbers to the right:

```
print(f"Pi to two decimal places is {3.1415926:1.3}")
value = 3.1415926
width = 1
precision = 3
print(f"Pi to two decimal places is: {value:{width}.{precision}}")
value = 3.1415926
width = 10
precision = 3
print(f"Pi to two decimal places is: {value:{width}.{precision}}")
```

## Multiline Strings

```
name = 'Nina'
pi = 3.14
food = 'pie'
message = (
    f"Hello, my name is {name}. "
    f"I can calculate pi to two places: {pi:4.3}. "
    f"But I would rather be eating {food}."
)
print(message)
```

## Trimming a string

strip() returns a new string after removing any leading and trailing whitespace. 
rstrip() and does the same but only removes trailing whitespace, and 
lstrip() only trims leading whitespace. 

```
my_string = "   Hello World!   "
print(f">{my_string.lstrip()}<")
print(f">{my_string.rstrip()}<")
>   Hello World!<
print(f">{my_string.strip()}<")
```

## Replacing Characters

replace() on any string and pass in what you want replace, and what you want to replace it with:

```
my_string = "Hello, world!"
my_string.replace("world", "Nina")
```

## str.format() and % formatting

```
name = "Nina"
print("Hello, my name is {name}".format(name=name))
```
