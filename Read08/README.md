# class-08

## List Comprehensions

List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.

---

### ingredients are necessary for a python list comprehension to work

* expression inside the square brackets.
* item inside the square brackets.
* we need an iterable list of objects to build our new list from.

---

#### Notes about Lists Comprehensions

* List comprehension methods are an elegant way to create and manage lists.
* In Python, list comprehensions are a more compact way of creating lists.
* More flexible than for loops, list comprehension is usually faster than other methods

---

### Create a List with range and for loop

![Create list with range and for loop ](https://blog.finxter.com/wp-content/uploads/2020/06/graphic.jpg)

---

### Multiplication with list comprehensions

![Multiplication with list comprehensions](https://4.bp.blogspot.com/-uRPZqKbIGwQ/XRtgWhC6qqI/AAAAAAAAH0w/--oGnwKsnpo00GwQgH2gV3RPwHwK8uONgCLcBGAs/s1600/comprehension.PNG)

---

### Separating the characters in a string

```letters = [ letter for letter in "20,000 Leagues Under The Sea"]
print(letters)
['2', '0', ',', '0', '0', '0', ' ', 'L', 'e', 'a', 'g', 'u', 'e', 's', ' ', 'U', 'n', 'd', 'e', 'r', ' ', 'T', 'h', 'e', ' ', 'S', 'e', 'a']
```

---

### Lower/Upper case

```lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]

### Identify numbers in a string using the isdigit()

phone_number = [ x for x in user_data if x.isdigit()]`


print(phone_number)

['9', '8', '7', '6', '5', '4', '3', '2', '1', '0']
```
