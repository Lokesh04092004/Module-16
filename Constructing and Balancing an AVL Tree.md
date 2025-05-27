
Ex. No: 16B - Constructing and Balancing an AVL Tree in Python

AIM:
To write a Python program to construct an **AVL tree**, balance it, and print the nodes **before and after balancing** using the appropriate packages and built-in function.

ALGORITHM:
1. Define Node Structure
Create a class for nodes with value, left, right, and height.

2. Insert Node (Standard BST Insertion)
Recursively insert based on BST rules.

3. Update Height
After insertion, update height of each ancestor node.

4. Get Balance Factor
For each node, compute:
balance = height(left) - height(right)

5. Balance the Node
Perform rotations based on balance:

Left Left Case → Right Rotation

Right Right Case → Left Rotation

Left Right Case → Left-Right Rotation

Right Left Case → Right-Left Rotation

6. In-order Traversal
To display the tree contents.


PYTHON PROGRAM
```
from TreeAVL.AVL import AVL
def getDictTree(self):
    return self.dict_tree
def Construct_AVL(L):
    tree=AVL(L)
    print(getDictTree(tree))
L=[12,8,18,5,11,17,4,7,2]
```

OUTPUT
![image](https://github.com/user-attachments/assets/06b9f1c2-ba96-429b-9751-7509d4c9cc49)

RESULT
Thus, Python program to construct an **AVL tree**, balance it, and print the nodes **before and after balancing** using the appropriate packages and built-in function was successfully implemented and verified.
