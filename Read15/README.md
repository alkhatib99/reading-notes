# class 15 - Trees

## Tree

<img src='https://res.cloudinary.com/practicaldev/image/fetch/s--od-naD9n--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://miro.medium.com/max/975/1%2APWJiwTxRdQy8A_Y0hAv5Eg.png'/>

### Traversals

Traversing a tree allows us to search for a node, print out the contents of a tree, and much more! There are two categories of traversals when it comes to trees:

* Depth First
* Breadth First

#### Depth First

Depth-first traversal is where we prioritize going through the depth (height) of the tree first. There are multiple ways to carry out depth first traversal,

<img src='https://cncws.github.io/uploads/image/leetcode/traversal.png'/>

#### pre_order

Pre-order means that the root has to be looked at first. In our case, looking at the root just means that we output its value. When we call preOrder for the first time,

#### Traversal Pseudocode

Here is the pseudocode for all three of the depth first traversals:
ALGORITHM preOrder(root)<br>
// INPUT <-- root node<br>
// OUTPUT <-- pre-order output of tree node's values<br>
    OUTPUT <-- root.value<br>
    if root.left is not Null<br>
        preOrder(root.left)<br>
    if root.right is not NULL<br>
        preOrder(root.right)<br>

<img src='https://image.slidesharecdn.com/bst-150422084019-conversion-gate02/95/binary-search-tree-9-638.jpg'/>

#### Breadth First

Breadth-first traversal iterates through the tree by going through each level of the tree node-by-node. So, given our starting tree one more time:

### Binary Search Trees

A Binary Search Tree (BST) is a type of tree that does have some structure attached to it. In a BST, nodes are organized in a manner where all values that are smaller than the root are placed to the left, and all values that are larger than the root are placed to the right.

#### Searching a BST

Searching a BST can be done quickly because all you do is compare the node you are searching for against the root of the tree or sub-tree. If the value is smaller
