
Ex. No: 16A - Constructing and Printing an AVL Tree in Python

AIM:
To write a Python program to construct an **AVL tree** and print the nodes of it using the appropriate packages and built-in function.


ALGORITHM:

Step 1: Define the AVL Node Structure
Each node should store:

value

left and right children

height of the node (for balancing)

Step 2: Define Helper Functions
get_height(node) – Returns height of a node.

get_balance(node) – Returns balance factor.

left_rotate(node) – Rotates the subtree left.

right_rotate(node) – Rotates the subtree right.

Step 3: Insert into the AVL Tree
Recursively insert like in a binary search tree.

Update height of ancestors.

Calculate balance factor and perform rotations if needed:

Left-Left → Right rotate

Right-Right → Left rotate

Left-Right → Left-Right rotate

Right-Left → Right-Left rotate

Step 4: Print the Tree
Use in-order traversal to print nodes in sorted order.


PYTHON PROGRAM
```
from TreeAVL.AVL import AVL

def getDictTree(self):
 return self.dict_tree

def Construct_AVL(L):
  tree = AVL(L)
  print(getDictTree(tree))

L=[12,8,18,5,11,17,4,7,2]

```

OUTPUT
![image](https://github.com/user-attachments/assets/ac349eb2-5f01-4e83-8b9a-4288a07525ac)

RESULT
Thus,Python program to construct an **AVL tree** and print the nodes of it using the appropriate packages and built-in function was successfully implemented and verified.
