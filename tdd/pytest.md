# PyTest

- PyTest is a python unit testing framework.
- It provides the ability to create Tests, Test Modules, and Test Fixtures.
- Uses the built-in Python assert statement.
- Has command line parameters to help filter which tests are executed and in what order.

## Creating a Test

- Tests are python functions with "test" at the beginning of the function name.
- Tests do verification of values using the standard python assert statement.
- Similar tests can be grouped together by including them in the same module or class.

## Test Discovery

- PyTest will automatically discover tests when you execute based on a standard naming convention.
- Test functions should include "test" at the begining of the function name.
- Classes with tests in them should have "Test" at the beginning of the class name and not have an "__init__" method.
- Filenames of test modules should start or end with "test". (i.e. test_example.py or example_test.py)

## XUnit Style Setup and Teardown

## Command

`pytest -v`
