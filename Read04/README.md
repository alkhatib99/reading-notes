# Classes and Objects

**Objects**
  Are an encapsulation of variables and functions into a single entity.
  Objects get their variables and functions from classes.
  Classes are essentially a template to create your objects.

---

## Accessing Object Variables

   To access the variable inside of the newly created object "myobjectx" you would do the following:

   `class MyClass:`
   `variable = "blah"`

   ` def function(self): `
   `print("This is a message inside the class.")`

 `myobjectx = MyClass()`

` myobjectx.variable `

## Accessing Object Functions

   To access a function inside of an object you use notation similar to accessing a variable:
  `myobjectx.function()`

### init()

The **init**() function, is a special function that is called when the class is being initiated. It's used for asigning values in a class.

## Thinking Recursively in Python

### Recursive Functions in Python

    A recursive function is a function defined in terms of itself via self-referential expressions.
    All recursive functions share a common structure made up of **two parts: base case and recursive case**

### Maintaining State

When dealing with recursive functions, keep in mind that each recursive call has its own execution context, so to maintain state during recursion you have to either:

- Thread the state through each recursive call so that the current state is part of the current call’s execution context
- Keep the state in global scope

### Recursive Data Structures in Python

A data structure is recursive if it can be deﬁned in terms of a smaller version of itself.

## Python Testing with pytest: Fixtures and Coverage

### Fixtures

Software test fixtures initialize test functions. They provide a fixed baseline so that tests execute reliably and produce consistent, repeatable, results

### Code coverage testing for Python

Coverage.py measures code coverage, typically during test execution.
It uses the code analysis tools and tracing hooks provided in the Python standard library to determine which lines are executable, and which have been executed.
