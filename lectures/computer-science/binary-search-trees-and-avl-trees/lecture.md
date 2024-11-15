# Binary Search Trees and AVL Trees

A **Binary Search Tree (BST)** is a node-based binary tree data structure where each node has a comparable key and an associated value. While searching, the desired key is compared to the keys in the BST and if found, the associated value is retrieved.

Example of a Binary Search Tree:

```python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key

def insert(root, key):
    if root is None:
        return Node(key)
    else:
        if root.val < key:
            root.right = insert(root.right, key)
        else:
            root.left = insert(root.left, key)
    return root

r = Node(50)
r = insert(r, 30)
r = insert(r, 20)
r = insert(r, 40)
r = insert(r, 70)
r = insert(r, 60)
r = insert(r, 80)
```

An **AVL Tree** is a type of binary search tree where the difference between heights of left and right subtrees cannot be more than one for all nodes to balance the tree.

Example of an AVL tree:

```python
class TreeNode(object):
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None
        self.height = 1

class AVL_Tree(object):

    def insert(self, root, key):
        
        # Step 1 - Perform normal BST
        if not root:
            return TreeNode(key)
        elif key < root.val:
            root.left = self.insert(root.left, key)
        else:
            root.right = self.insert(root.right, key)
        
        # Step 2 - Update the height of the 
        # ancestor node
        root.height = 1 + max(self.getHeight(root.left),
                           self.getHeight(root.right))
        
        # Step 3 - Get the balance factor
        balance = self.getBalance(root)
        
        # Step 4 - If the node is unbalanced, 
        # then try one of the 4 cases
        # Case 1 - Left Left
        if balance > 1 and key < root.left.val:
            return self.rightRotate(root)
        
        # Case 2 - Right Right
        if balance < -1 and key > root.right.val:
            return self.leftRotate(root)
        
        # Case 3 - Left Right
        if balance > 1 and key > root.left.val:
            root.left = self.leftRotate(root.left)
            return self.rightRotate(root)
        
        # Case 4 - Right Left
        if balance < -1 and key < root.right.val:
            root.right = self.rightRotate(root.right)
            return self.leftRotate(root)
        
        return root
```

In both cases, operations such as insertion, deletion, and searching have average and worst-case complexity of O(log n). They are powerful tools in computer science and have many applications including database indexing and priority queues.