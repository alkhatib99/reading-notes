# Linked List

A Linked List is a sequence of Nodes that are connected/linked to each other. The most defining feature of a Linked List is that each Node references the next Node in the link.
 There are two types of Linked List - Singly and Doubly.  

 he best way to approach a traversal is through the use of a while() loop. This allows us to continually check that the Next node in the list is not null. If we accidentally end up trying to traverse on a node that is null, a NullReferenceException gets thrown and our program will crash/end.

When traversing through a linked list, the Current variable will tell us where exactly in the linked list we are and will allow us to move/traverse forward until we hit the end.

---

## ***What’s a Linked List

 One characteristic of linked lists is that they are linear data structures, which means that there is a sequence and an order to how they are constructed and traversed. 
 The biggest differentiator between arrays and linked lists is the way that they use memory in our machines. 

---

 inserting an element at the end of a linked list is a different story. The interesting thing here is that the steps you take to actually do the inserting are the exact same:

 1. Find the node we want to change the pointer of (in this case, the last node)
 2. Create the new node we want to insert and set its pointer (in this case, to null)
 3. Direct the preceding node’s pointer to our new node

 inserting an element at the end of a linked list is a different story. The interesting thing here is that the steps you take to actually do the inserting are the exact same:
 Find the node we want to change the pointer of (in this case, the last node)
 Create the new node we want to insert and set its pointer (in this case, to null)
 Direct the preceding node’s pointer to our new node

![Image](https://res.cloudinary.com/practicaldev/image/fetch/s--y3j6aJXJ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://res.cloudinary.com/practicaldev/image/fetch/s--_PwtVEkJ--/c_limit%252Cf_auto%252Cfl_progressive%252Cq_auto%252Cw_880/https://www.educative.io/api/edpresso/shot/5077575695073280/image/5192456339456000)

---

## Why Linked List?

> - Arrays can be used to store linear data of similar types, but arrays have the following limitations.
> - The size of the arrays is fixed: So we must know the upper limit on the number of elements in advance. Also, generally, the allocated memory is equal to the upper limit irrespective of the usage.
> - Inserting a new element in an array of elements is expensive because the room has to be created for the new elements and to create room existing elements have to be shifted.
> - A linked list is created by using the node class. We create a Node object and create another class to use this ode object. We pass the appropriate values thorugh the node object to point to the next data elements. The below program creates the linked list with three data elements.

![Image](https://miro.medium.com/max/1050/1*cUehR5S18XSoVLaPNfNzlA.jpeg)

---

## Implementation: Linked Lists

### ***Big O: Analysis of Algorithm Efficiency***

Big O(oh) notation is used to describe the efficiency of an algorithm or function. This efficiency is evaluated based on 2 factors:

 1. Running Time (also known as time efficiency / complexity)
 The amount of time a function needs to complete.

 2. Memory Space (also known as space efficiency / complexity)
 The amount of memory resources a function uses to store data and instructions.

 Big O’s role in algorithm efficiency is to describe the Worst Case of efficiency an algorithm can have in performing it’s job. It specifically looks at the factors mentioned above, which we often refer to as Space and Time. In order to analyze these limiting factors, we should consider 4 Key Areas for analysis:

 1. Input Size
 2. Units of Measurement
 3. Orders of Growth
 4. Best Case, Worst Case, and Average Case

 Always be aware that Space Complexity and Time Complexity are measured differently and should be analyzed separately. It’s also worth noting that contemporary computing affords most machinees with multiple GigaBytes of working memory, so algorithm space complexity is not as much of a concern as it used to be.