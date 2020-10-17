# Exceptions

Built-in exceptions and easy exception handling is one of the shining features of Python. Technically, errors that happen during parsing are called SyntaxErrors - these will probably be the most common errors you see, and usually happen because of a mistake in whitespace, a syntax misunderstanding, or a simple typo.

Even if the syntax is correct, errors can still occur when your program is run. We call these Exceptions, and there a many different types (this is a good thing, because the more specifically we know what went wrong, the better we can handle it).

An un-handled exception is fatal: it will print debugging information (called a traceback), stop the interpreter, and exit your program. However, once you learn to handle Exceptions, you can cover your bases and write programs that are robust in the face of issues.

## Types of Exceptions

AttributeError:	    Raised when attribute assignment or reference fails.
ImportError:	      Raised when the imported module is not found.
IndexError:	        Raised when index of a sequence is out of range.
KeyError:	          Raised when a key is not found in a dictionary.
KeyboardInterrupt:	Raised when the user hits interrupt key (Ctrl+c or delete).
NameError:	        Raised when a variable is not found in local or global scope.
SyntaxError:	      Raised by parser when syntax error is encountered.
IndentationError:	  Raised when there is incorrect indentation.
ValueError:	        Raised when a function gets argument of correct type but improper value.

## Exception Hierarchy

ZeroDivisionError is a subclass of ArithmeticError, which is a subclass of Exception, itself a subclass of BaseException.
You could use except Exception, but this is not a good idea, as it will catch almost every type of error, even ones you weren’t expecting. 

[Full chart of the hierarchy for built-in exceptions](https://docs.python.org/3/library/exceptions.html#exception-hierarchy)

## Exiting your Program

As we mentioned, exceptions that are allowed to bubble up to the top level (called unhandled exceptions) will cause your program to exit. This is generally unwanted - even if an error is unrecoverable, we still want to provide more detailed information about the error for later inspection, or a pretty error for the user if our program is user-facing, and in most cases, we want the program to go back to doing what it was doing.

You can also use sys.exit() from the built-in sys library. It’s generally not a good idea to pepper sys.exit() around your code, as it makes it harder to control when your program exits, but this can be a handy function for controlling how and when your program exits. By default, sys.exit() with no parameters will exit with a 0 return code, which, by posix convention, signals success. You can pass an integer to sys.exit() if you’d like to exit with a non-zero return code (usually signaling some sort of failure condition). You can also pass a string to sys.exit(), which will get printed to the command line, along with a return code of 1.

sys.exit() generates a SystemExit exception, which inherits from the master BaseException class, which makes it possible for clean-up handlers (such as finally statements) to run.

## TRY EXCEPT

Python uses four keywords: `try, except, else, and finally`. 

Code that can possibly throw an exception goes in the try block. except gets the code that runs if an exception is raised. else is an optional block that runs if no exception was raised in the try block, and finally is an optional block of code that will run last, regardless of if an exception was raised. 

```
try:
    # Code to try

except (RuntimeError, TypeError, NameError):
    # Code to run if one of these exceptions is hit
```

A try statement can also have more than one except clause
```
try:
    # Code to try

except RuntimeError:
    # Code to run if there's a RuntimeError

except TypeError:
    # Code to run if there's a TypeError

except NameError:
    # Code to run if there's a NameError
```

finally is an optional block that runs after try, except, and else, regardless of if an exception is thrown or not. This is good for doing any cleanup that you want to happen, whether or not an exception is thrown.
```
try:
    raise KeyboardInterrupt
finally:
    print("Goodbye!")
```

## BEST PRACTICES

Catch More Specific Exceptions First.
> except handlers are evaluated in order, so be sure to put more specific exceptions first.

Don’t Catch `Exception`
> You may have errors that you don’t care about, and don’t affect the operation of your program, or maybe you’re dealing with a flaky API and want to swallow errors and retry.
> By catching Exception, you run the risk of hitting an unexpected exception that your program actually can’t recover from, or worse, swallowing an important exception without properly logging it - a huge headache when trying to debug programs that are failing in weird ways.

Definitely don’t catch `BaseException`

## CUSTOM EXCEPTIONS

```
class MyCustomException(Exception):
    pass
raise MyCustomException()
```

```
    def __init__(self, value):
        message = f"Got an incorrect value of {value}"
        super().__init__(message)
my_value = 9999
if my_value > 100:
    raise IncorrectValueError(my_value)
```

A Custom Exception for our GitHub API app
```
class GitHubApiException(Exception):

    def __init__(self, status_code):
        if status_code == 403:
            message = "Rate limit reached. Please wait a minute and try again."
        else:
            message = f"HTTP Status Code was: {status_code}."

        super().__init__(message)
```