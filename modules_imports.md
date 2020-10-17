# Modules & Imports

Python has a simple package structure. Any directory with a file named __init__.py can be considered a Python module.

> a __init__.py file is no longer required for Python 3 modules, but it’s still supported and can be useful.

## Best Practices

Don't import everything from a module into the local namespace using *
> This isn’t a good practice, because it’s hard to tell where a specific function is coming from without the namespace context. Also, function names can conflict, and this can make things very difficult to debug.

Better is to import functions specifically
```
from my_math_functions import add_numbers
add_numbers(1, 2)
```

You can use the as keyword to make things a little easier on yourself.
```
import my_math_functions as mmf
mmf.add_numbers(1, 2)
```

## PYTHONPATH

This is a list of paths on your system where Python will look for packages. Python will always look first in the working directory (the folder you’re in when you start the REPL or run your program), so if your module folder is there, you can import it. You can also install your modules just like any other external modules, using a setup.py file. It’s also possible to change or add paths to your PYTHONPATH list if you need to store modules elsewhere, but this isn’t a very portable solution.

## PYPI

PyPI (the Python Package Index) is an awesome service that helps you find and install software developed and shared by the Python community. Almost every user-contributed Python package has been published to PyPI.

There are a lot of packages on PyPI, and they’re not always up-to-date. Sometimes it helps to look at a package before installing it. Simply search for a package name on PyPI.org