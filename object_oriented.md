# Object Oriented Programming

Object-oriented Programming (OOP) is a language model (or paradigm) in which properties or behaviors are organized into “objects”. Some languages encourage a more procedural style, like if you were writing a recipe - some popular examples are COBOL and BASIC. Languages that adopt an Object-oriented style organize things into objects, and provide methods for objects to communicate with one another.

An object can be a function, a variable, a property, a class… everything in Python is an object. You can think of an object as a generic container - a list object might contain a sequence of int objects, along with some function objects. The int objects contain integer numbers. The function objects contain code that can be executed on the list object or maybe on the items in the list.

Every thing or object in Python is an instance of a class. The number 42 is an instance of the class int. The string Hello, world is an instance of the str (or string) class. These classes, in turn, are subclasses of the master object class.

## Classes vs Instances

You can think of a class as a “type” of something, like “Car.” You can think of an instance as a specific thing, such as “my Subaru,” which is a type of “Car.”

Both classes and instances can have variables and methods. Changing a class variable will change what is returned when you get that variable from an instance, however changing an instance variable only applies to that one instance.

## self

self is used inside classes to refer to a bound instance variable or object.
self refers to an instance

## type, isinstance, and issubclass

## __init__

You can use the __init__() method to do any special thing you want to happen when your instance is instantiated, including setting instance variables. __init__ can take arguments, too.

> Methods that are bracketed by underscores are sometimes called “magic methods.”

## __str__ and __repr__

__str__() and __repr__(). Both functions return a string representation of an object. __str__() should return readable end-user output, and __repr__() should return the Python code necessary to rebuild the object. __str__() maps to the built-in function str() and __repr__() maps to the built-in function repr().

```
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def __str__(self):
        return f"<<Car object: {self.make} {self.model}>>"

    def __repr__(self):
        return f"Car('{self.make}', '{self.model}')"
```

## Inheritance

Inheritance makes it possible to break up and organize your code into a hierarchy, from generic to specific. Objects that belong to classes that are higher up in the hierarchy (more generic) are accessible by subclasses, but not vice versa.

```
class Vehicle:

    def __init__(self, make, model, fuel="gas"):
        self.make = make
        self.model = model
        self.fuel = fuel

class Car(Vehicle):

    def __init__(self, make, model, fuel="gas"):
        super().__init__(make, model, fuel)
```

We can, of course, use a subclass to override variables that belong to a parent class. 

```
class Vehicle:
    number_of_wheels = 4

    def __init__(self, make, model, fuel="gas"):
        self.make = make
        self.model = model
        self.fuel = fuel

class Car(Vehicle):

    def __init__(self, make, model, fuel="gas"):
        super().__init__(make, model, fuel)

class Truck(Vehicle):
    number_of_wheels = 6

    def __init__(self, make, model, fuel="diesel"):
        super().__init__(make, model, fuel)

class Motorcycle(Vehicle):
    number_of_wheels = 2
```

> Note how our Truck’s class variable number_of_wheels overrode the parent class Vehicle’s number_of_wheels (or, to be more specific, the interpreter found number_of_wheels in a closer scope, the Truck class, and did not need to continue searching up the hierarchy).

## Multiple Inheritance

One common use case for multiple inheritance in Python is for a type of class called a Mixin. 
Mixin classes tend to be used to quickly and easily add additional properties and methods into a class. This type of design pattern encourages code with composable architecture.