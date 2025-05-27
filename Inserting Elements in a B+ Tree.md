
Ex. No: 16D - Inserting Elements in a B+ Tree in Python

AIM:
To write a Python function `def insert(self, key, value):` to insert elements into a **B+ Tree**.


ALGORITHM:
Start at the root node.

If the root is full (has t - 1 keys):

Create a new node new_root.

Make the old root a child of new_root.

Split the old root node into two nodes.

Promote the middle key to new_root.

Update the root to be new_root.

Insert the key into a non-full node:

If the node is a leaf node:

Find the correct position to insert the (key, value) pair, keeping keys sorted.

Insert (key, value) into the leaf.

If the node is an internal node:

Find the child node to which the key belongs (the correct subtree).

If the child node is full (has t - 1 keys):

Split the child node.

Promote the middle key from the child to the current node.

Re-determine the correct child to descend into (because of the split).

Recursively insert the key into the child node.

Splitting a node:

For a node with 2t - 1 keys (overflow condition), split it into two nodes:

Left node: contains first t - 1 keys.

Right node: contains remaining keys.

For internal nodes, promote the middle key to the parent node.

For leaf nodes, promote the first key of the right node to the parent node (since all actual keys are stored in leaves).

Adjust pointers (for leaf nodes, update sibling pointers).

Repeat the process until the key is inserted and the tree is balanced.



PYTHON PROGRAM

```
class Node(object):
    
    def __init__(self, order):
        
        self.order = order
        self.keys = []
        self.values = []
        self.leaf = True

    def add(self, key, value):
        
        if not self.keys:
            self.keys.append(key)
            self.values.append([value])
            return None

        for i, item in enumerate(self.keys):
            
            if key == item:
                self.values[i].append(value)
                break

            
            elif key < item:
                self.keys = self.keys[:i] + [key] + self.keys[i:]
                self.values = self.values[:i] + [[value]] + self.values[i:]
                break

        
            elif i + 1 == len(self.keys):
                self.keys.append(key)
                self.values.append([value])

    def split(self):
        
        left = Node(self.order)
        right = Node(self.order)
        mid = self.order // 2

        left.keys = self.keys[:mid]
        left.values = self.values[:mid]

        right.keys = self.keys[mid:]
        right.values = self.values[mid:]

      
        self.keys = [right.keys[0]]
        self.values = [left, right]
        self.leaf = False

    def is_full(self):
     
        return len(self.keys) == self.order

    def show(self, counter=0):
        
        print(counter, str(self.keys))

        
        if not self.leaf:
            for item in self.values:
                item.show(counter + 1)

class BPlusTree(object):
    
    def __init__(self, order=8):
        self.root = Node(order)

    def _find(self, node, key):
        
        for i, item in enumerate(node.keys):
            if key < item:
                return node.values[i], i

        return node.values[i + 1], i + 1

    def _merge(self, parent, child, index):
        
        parent.values.pop(index)
        pivot = child.keys[0]

        for i, item in enumerate(parent.keys):
            if pivot < item:
                parent.keys = parent.keys[:i] + [pivot] + parent.keys[i:]
                parent.values = parent.values[:i] + child.values + parent.values[i:]
                break

            elif i + 1 == len(parent.keys):
                parent.keys += [pivot]
                parent.values += child.values
                break

    def insert(self, key, value):
        parent = None
        child = self.root

        while not child.leaf:
            parent = child
            child, index = self._find(child, key)

        child.add(key, value)

        
        if child.is_full():
            child.split()

           
            if parent and not parent.is_full():
                self._merge(parent, child, index)
        
        
        
        
        
        
        
        
        
        
        
        

    def retrieve(self, key):
       
        child = self.root

        while not child.leaf:
            child, index = self._find(child, key)

        for i, item in enumerate(child.keys):
            if key == item:
                return child.values[i]

        return None

    def show(self):
        
        self.root.show()

def demo_node():
    node = Node(order=4)
    node.add('a', 'alpha')
    node.add('b', 'bravo')
    node.add('c', 'charlie')
    node.add('d', 'delta')
    node.show()

    print('\nSplitting node...')
    node.split()
    node.show()

def demo_bplustree():
    print('B+ tree...')
    bplustree = BPlusTree(order=4)
    x=input()
    y=input()
    bplustree.insert('a', 'alpha')
    bplustree.insert('b', 'bravo')
    bplustree.insert('c', 'charlie')
    bplustree.insert('d', 'delta')
    bplustree.insert('e', 'echo')
    bplustree.insert(x,y)

    
    #write your code here
    
    
    bplustree.show()

    

if __name__ == '__main__':
    demo_node()
    print('\n')
    demo_bplustree()


```

OUTPUT
![image](https://github.com/user-attachments/assets/0311b1fd-e717-4d71-a613-6f2d873006f0)

RESULT
Thus, the  Python function `def insert(self, key, value):` to insert elements into a **B+ Tree** was successfully implemented and verified.
