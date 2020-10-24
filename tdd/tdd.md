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
