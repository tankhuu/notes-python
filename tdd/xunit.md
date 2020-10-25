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

## Yield

- The yield keyword is the simpler of the two options for teardown code.
- The code after the yield is executed after the fixture goes out of scope.
- The yield keyword is a replacement for return and any return values should be passed to it.

## Addfinalizer

- The addfinalizer method of adding teardown code is a little more complicated but also a little more capable than the yield statement.
- With the addfinalizer method one or more finalizer functions are added via the request-context’s addfinalizer method.
- One of the big differences between this method and the yield keyword method is that this method allows for multiple finalization functions to be specified.
- Now lets take a look at some examples.

> Which tests a fixture applies to and how often it is run depends on the fixture scope test fixtures

## Test Fixture have 4 Scopes

- Function - Run the fixture once for each test.
- Class - Run the fixture once for each class of tests.
- Module - Run once when the module goes in scope.
- Session - The fixture is run when pytest starts.

## Return Objects and Params

PyTest Test Fixtures allow you to optionally return data from the fixture that can be used in the test.

- The optional params array argument in the fixture decorator can be used to specify one or more values that should be passed to the test.
- When a params argument has multiple values then the test will be called once with each value.

```
@pytest.fixture(params=[1,2])
def setupData(request):
  return request.param
def test1(setupData):
  print(setupData)
```

## Command line Arguments

-v Report in verbose mode
-q run in quiet mode (helpful when run hundreds or thousands tests at once)
-s don't capture console output (show print statements on the console)
--ignore Ignore the specified path when discovering tests.
--maxfail Stop after the specified number of failures.

```
pytest -v -s -k "test2 or test3"
pytest -v -s -m "test1 or test3"
```
