# Testing and Modules

---

## Unit tests

**some pieces of code to exercise the input, the output and the behaviour of your code.**
> to see if the your is working in the right way

---

### Important aspects about the unit test

- The test name : it should describe what we are testing and what it should return or expect from it

the file name :The test file name should follow the same name of module name.

module.py ==> test_module.py

- Arrange: you need to organize the data needed to execute that piece of code (input);

- Act: here you will execute the code being tested (exercise the behaviour);

- Assert: after executing the code, you will check if the result (output) is the same as you were expecting.

---

### The Cycle

🆘 Write a unit test and make it fail

✅ Write the feature and make the test pass!

🔵 Refactor the code

---

### `if __name__ == “__main__”:`

module :module is a file containing Python definitions and statements.

example :

print ("Always executed") 
`if __name__ == "__main__":`
    print ("Executed when invoked directly")

else:
    print ("Executed when imported")

---

### Recursion

*when a function calls itself directly or indirectly*

*we can use recursion to solve problems easily*

- base condition :
    The base is the solution of the problem 
  we devide the problem into smaller ones till it reach the base case stop the recursion*
