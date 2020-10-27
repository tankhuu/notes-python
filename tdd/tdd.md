# Unit Test

3 steps:

- Setup: creates test string.
- Action: call production code to perform the action that's under test.
- Assert: where the test validates results of the action.

## Test Driven Development (TDD)

A process where the developer takes personal responsibility for the quality of their code.
Unit Tests are written before the production code.
Don't write all the tests or production code at once.
-> You write 1 unittest for 1 testcase and then you write the production code to make it pass
Test and production code are both written together in a small bits of functionality.

## TDD Workflow

- RED: write a failing unit test
- GREEN: write just enough production code to make that test pass
- REFACTOR: cleanup the unit test and production code to remove any duplication, make sure the code follows your team's coding standards and best practices.
- REPEAT: the process for all the functionality you need to implement and all the positive and negative test cases.

## Uncle BOB's 3 Laws of TDD

- You may not write any production code until you have written a failing unit test.
- You may not write more of the unit test than is sufficient to fail, and not compiling is failing.
- You may not write more production code than is sufficient to pass the currently failing unit test.

## Test Doubles

- Almost all code that gets implemented will depend on another piece of code in the system.
- Those other pieces of code are often times trying to do things or communicate with things that are not available in the unit testing environment, or are so slow that they would make our unit tests extremely slow. For example, if you’re code queries a 3rd party REST API on the internet and that server is down for any reason you can’t run your tests.
- Test doubles are the answer to that problem. They are objects created in the test to replace the real production system collaborators.
- There are many types of test doubles.
  - _Dummy_ objects are the simplest. They are simply placeholders that are intended to be passed around but not actually called or used in any real way. They will often generate exceptions if they are called.
  - _Fake_ objects have a different (and usually simplified) implementation from the production collaborator that make them useable in the test code but not suitable for production.
  - _Stubs_ provide implementations that do expect to be called but respond with basic canned responses.
  - _Spies_ provide implementations that record the values that are passed in to them. The tests can then use those recorded values for validating the code under test.
  - _Mock_ objects are the most sophisticated of all the test doubles. They have pre-programmed expectations about the ordering of calls, the number of times functions will be called, and the values that will be passed in. Mock objects will generate their own exceptions when these pre-programmed expectations are not met.

> We should use Mock for Test Doubles

### Mock Frameworks

- Mock frameworks are libraries that provide easy to use API’s for automatically creating any of these types of test doubles AT RUNTIME.
- They provide easy API’s for specifying the mocking expectations in your unit tests.
- They can be much more efficient than implementing your own custom mock objects.
- As creating your own custom mock objects can be time consuming, tedious, and error prone.

### PyTest Monkeypatch Test Fixture

- PyTest provides the monkeypatch test fixture to allow a test to dynamically change:
- Module and class attributes
- Dictionary entries
- And Environment Variables
- Unittest provides a patch decorator which performs similar operations but this can sometimes conflict with the PyTest TestFixture decorators so I’ll focus on using monkeypatch for this functionality.

### unittest.mock is a mocking framework for Python.

- unittest.mock is a mocking framework for Python.
- Unittest.mock provides the Mock class which is an extremely power class that be used to create test objects that can be used as fakes, stubs, spies, or true mocks for other classes or functions.
- The Mock class has many initialization parameters for specifying how the object should behave such as what interface it should mock, if it should call another function when it is called, or what value it should return.
- Once a Mock object has been used it has many built-in functions for verifying how it was used such as how many times it was called and with what parameters.

```
# Example
def test_Foo():
bar = Mock() functionThatUsesBar( bar ) bar.assert_called_once()
```

- Mock provides many initialization parameters which can be used to control the mock object’s behavior.
- The spec parameter specifies the interface that the Mock object is implementing. If any attributes of the mock object are called which are not in that interface then the
- Mock will automatically generate an AttributeError exception.
- The side_effect parameter specifies a function that should be called when the mock is called. This can be useful for more complicated test logic that returns different values depending on input parameters or generates exceptions.
- The return_value parameter specifies the value that should be returned when the mock object is called. If the side_effect parameter is set it’s return value is used instead.

```
# Example
def test_Foo(): •
bar = Mock(spec=SpecClass) bar2= Mock(side_effect=
barFunc) • bar3 = Mock(return_value=1)
```
