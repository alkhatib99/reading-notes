# Reading and Writing Files in Python

---

## What Is a File?

a file is a contiguous set of bytes used to store data ( which can be as simple as a text file or as complicated as a program executable)
**File parts**

- Header: metadata about the contents of the file (file name, size, type, and so on)

- Data: contents of the file as written by the creator or editor

- End of file (EOF): special character that indicates the end of the file

**File Paths**
The file path is a string that represents the location of a file (Folder Path  / File Name / Extension )

**Line Endings**
how to representation of a new line or line ending.
Windows uses the CR+LF characters to indicate a new line, while Unix and the newer Mac versions use just the LF character

**Character Encodings**
An encoding is a translation from byte data to human readable characters.
This is typically done by assigning a numerical value to represent a character.
The two most common encodings are the ASCII and UNICODE Formats.

---

### Opening and Closing a File in Python

work with file steps :
1- open the file .open() with modes ( r / w / rb / wb ) 
2- to make sure the file will be closed even if the user forget or error ocured we use the command try-finally or with statement

**file objects**
file object is  an object exposing a file-oriented API (with methods such as read() or write()) to an underlying resource.
types:

- Text files , open() will return a TextIOWrapper file object
- Buffered binary files , open() will return either a BufferedReader or BufferedWriter file object.
- Raw binary files , open() will return a FileIO file object

---

### Writing on file

**.write(string)**
  This writes the string to the file.

**.writelines(seq)**
  This writes the sequence to the file. No line endings are appended to each sequence item. 
It’s up to you to add the appropriate line ending(s).

---

## Python Exceptions: An Introduction

### Exceptions versus Syntax Errors

  Syntax errors occur when the parser detects an incorrect statement
  exception error occurs whenever syntactically correct Python code results in an error.

**Raising an Exception**
   If you want to throw an error when a certain condition occurs using raise .

**The AssertionError Exception**
   Instead of waiting for a program to crash midway, you can also start by making an assertion in Python. 

**The try and except Block: Handling Exceptions**
   The try and except block in Python is used to catch and handle exceptions. 
   Python executes code following the try statement as a “normal” part of the program. 

**The else Clause**
   Using the else statement, you can instruct a program to execute a certain block of code only in the absence of exceptions.

**Cleaning Up After Using finally**
   Everything in the finally clause will be executed. It does not matter if you encounter an exception somewhere in the try or else clauses.
