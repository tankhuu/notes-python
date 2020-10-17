# Object Oriented Programming

Object-oriented Programming (OOP) is a language model (or paradigm) in which properties or behaviors are organized into “objects”. Some languages encourage a more procedural style, like if you were writing a recipe - some popular examples are COBOL and BASIC. Languages that adopt an Object-oriented style organize things into objects, and provide methods for objects to communicate with one another.

An object can be a function, a variable, a property, a class… everything in Python is an object. You can think of an object as a generic container - a list object might contain a sequence of int objects, along with some function objects. The int objects contain integer numbers. The function objects contain code that can be executed on the list object or maybe on the items in the list.

Every thing or object in Python is an instance of a class. The number 42 is an instance of the class int. The string Hello, world is an instance of the str (or string) class. These classes, in turn, are subclasses of the master object class.

## Classes vs Instances

You can think of a class as a “type” of something, like “Car.” You can think of an instance as a specific thing, such as “my Subaru,” which is a type of “Car.”

Both classes and instances can have variables and methods. Changing a class variable will change what is returned when you get that variable from an instance, however changing an instance variable only applies to that one instance.

## self
