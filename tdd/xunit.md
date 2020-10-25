# XUnit Style Setup and Teardown

XUnit Style Setup/Teardown functions will execute code before and after:

- Test Modules
- Test Functions
- Test Classes

```
def setup_module():
def teardown_module():
def setup_function():
def teardown_function():
def setup_class():
def teardown_class():
```

Using setup/teardown functions can help to reduce code duplication by letting you specify the setup and teardown code once at each of the different levels as necessary rather than repeating the code in each individual unit tests.

With @classmethod decorator -> methods are passed in the uninstall initiated class object rather than a unique instance of the class.
The setup class method will be executed by tests before any of the unit tests in the class are executed.
The teardown class method will be executed by tests after all of the unit tests in the class are executed.
Setup method will be called before each unit test in the class is executed and the tear down method.
Teardown method will be called after all of unit tests in the class is completed.

```
class TestClass:
  @classmethod
  def setup_class(cls):
    print("Setup TestClass!")

  @classmethod
  def teardown_class(cls):
    print("Teardown TestClass!)

  def setup_method(self, method):
    if method == self.test1:
      print("\nSetting up test1!")
    elif method == self.test2:
      print("\nSetting up test2!")
    else:
      print("\nSetting up unknown test!")

  def teardown_method(self, method):
    if method == self.test1:
      print("\nTeardown up test1!")
    elif method == self.test2:
      print("\nTeardown up test2!")
    else:
      print("\nTeardown up unknown test!")

  def test1(self):
    print("Executing test1!")
    assert True

  def test2(self):
    print("Executing test2!")
    assert True
```

## Test Fixtures

- Test Fixtures allow for reuse of setup and teardown code across tests.
- The 'pytest.fixture' decorator is applied to functions that are decorators.
- Individual unit tests can specify which fixtures they want executed.
- The autouse parameter can be set to true to automatically execute a fixture before each test.

```
@pytest.fixture():
def setup():
  print("\nSetup")

def test1(setup):
  print("Executing Test1!")
  assert True

@pytest.mark.usefixtures('setup')
def test2():
  print("Executing Test2!")
  assert True
```

- It can be very useful for each individual test to be able to specify which test fixtures it needs executed before the test is run.
- But this can also be cumbersome for those cases where all the tests need to run the same test fixture.

```
@pytest.fixture(autouse=True):
def setup():
  print("\nSetup")

def test1():
  print("Executing Test1!")
  assert True

def test2():
  print("Executing Test2!")
  assert True
```
