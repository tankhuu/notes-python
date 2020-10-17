# Testing in Python

Unit testing is a software testing method by which individual functions are tested in an automated fashion to determine if they are fit for use. Automated unit testing not only helps you discover and fix bugs quicker and easier than if you weren’t testing, but by writing them alongside or even before your functions, they can help you write cleaner and more bug-free code from the very start.

## Types of Tests

- Unit tests operate on the smallest testable unit of code, usually a function that performs a single action or operation.
- Integration tests check to see if different units or modules of code work together as a group.
- Functional tests operate on units of functionality, to make sure a specific function of the software is working, which may involve several units of software or whole systems working together.

## Assertions

An assertion is simply a boolean expression that checks if its conditions return true or not.
If the assertion is true, the program continues. If it’s false, it throws an AssertionError, and your program will stop.

```
input_value = 25
assert input_value > 0
```

> assert Is For Sanity Checks, Not For Production!

Assertions are great for simple self-checks and sanity tests. You shouldn’t, however, use assertions for failure cases that can occur because of bad user input or operating system/environment failures, such as a file not being found. These situations are much better suited to an exception or an error message.


## Writing Tests

```
import unittest

def multiply(x, y):
    return x * x

class TestMultiply(unittest.TestCase):

    def test_multiply(self):
        test_x = 5
        test_y = 10
        self.assertEqual(multiply(test_x, test_y), 50, "Should be 50")

if __name__ == "__main__":
    unittest.main()
```

[Nose2](https://nose2.readthedocs.io/en/latest/)

[PyTest](https://docs.pytest.org/en/latest/)
