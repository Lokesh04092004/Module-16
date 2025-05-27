
Ex. No: 16C - Inserting Nodes in a B-Tree in Python

AIM:
To write a Python function `def insert(self, k):` to insert the nodes in a **B-Tree**.

ALGORITHM:
Check if root is full.

If root has 2t - 1 keys, it is full.

Create a new node s as a new root and split the old root.

Insert the key into the appropriate child.

If root is not full, just call the recursive helper function to insert in a non-full node.



PYTHON PROGRAM
```
# Searching a key on a B-tree in Python


# Create a node
class BTreeNode:
  def __init__(self, leaf=False):
    self.leaf = leaf
    self.keys = []
    self.child = []


class BTree:
  def __init__(self, t):
    self.root = BTreeNode(True)
    self.t = t


  def insert(self, k):
    root=self.root
    if len(root.keys)==(2*self.t)-1:
        temp=BTreeNode()
        self.root=temp
        temp.child.insert(0,root)
        self.split_child(temp,0)
        self.insert_non_full(temp,k)
    else:
        self.insert_non_full(root,k)

  def insert_non_full(self, x, k):
    i = len(x.keys) - 1
    if x.leaf:
      x.keys.append((None, None))
      while i >= 0 and k[0] < x.keys[i][0]:
        x.keys[i + 1] = x.keys[i]
        i -= 1
      x.keys[i + 1] = k
    else:
      while i >= 0 and k[0] < x.keys[i][0]:
        i -= 1
      i += 1
      if len(x.child[i].keys) == (2 * self.t) - 1:
        self.split_child(x, i)
        if k[0] > x.keys[i][0]:
          i += 1
      self.insert_non_full(x.child[i], k)

  def split_child(self, x, i):
    t = self.t
    y = x.child[i]
    z = BTreeNode(y.leaf)
    x.child.insert(i + 1, z)
    x.keys.insert(i, y.keys[t - 1])
    z.keys = y.keys[t: (2 * t) - 1]
    y.keys = y.keys[0: t - 1]
    if not y.leaf:
      z.child = y.child[t: 2 * t]
      y.child = y.child[0: t - 1]

  # Print the tree
  def print_tree(self, x, l=0):
    print("Level ", l, " ", len(x.keys), end=":")
    for i in x.keys:
      print(i, end=" ")
    print()
    l += 1
    if len(x.child) > 0:
      for i in x.child:
        self.print_tree(i, l)

  

B = BTree(3)

for i in range(10):
    B.insert((i, 2 * i))
print("B Tree :")
B.print_tree(B.root)
n=int(input())
B.insert((n,))
# Write your code here

print("\nB Tree after insertion")
B.print_tree(B.root)
```

OUTPUT
![image](https://github.com/user-attachments/assets/74dc0111-e03d-4ee9-a485-eadb060f80d8)

RESULT
Thus,a Python function `def insert(self, k):` to insert the nodes in a **B-Tree** was successfully implemented and verified.
