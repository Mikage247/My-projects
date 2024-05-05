Example
‘’’
class TreeNode:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.height = 1
        self.val = key

def height(node):
    if not node:
        return 0
    return node.height

def update_height(node):
    node.height = 1 + max(height(node.left), height(node.right))

def balance_factor(node):
    if not node:
        return 0
    return height(node.left) - height(node.right)

def left_rotate(x):
    y = x.right
    T2 = y.left
    y.left = x
    x.right = T2
    update_height(x)
    update_height(y)
    return y

def right_rotate(y):
    x = y.left
    T2 = x.right
    x.right = y
    y.left = T2
    update_height(y)
    update_height(x)
    return x

def balance(node):
    if not node:
        return node

    update_height(node)
    balance = balance_factor(node)

    if balance > 1:
        if balance_factor(node.left) < 0:
            node.left = left_rotate(node.left)
            rotations.append('LR')
        node = right_rotate(node)
        rotations.append('RR')
    elif balance < -1:
        if balance_factor(node.right) > 0:
            node.right = right_rotate(node.right)
            rotations.append('RL')
        node = left_rotate(node)
        rotations.append('LL')
    
    return node

def insert(node, key):
    if not node:
        return TreeNode(key)
    elif key < node.val:
        node.left = insert(node.left, key)
    else:
        node.right = insert(node.right, key)
    return balance(node)

def find_leaves(root):
    leaves = []
    if root:
        if root.left is None and root.right is None:
            leaves.append(root.val)
        leaves += find_leaves(root.left)
        leaves += find_leaves(root.right)
    return leaves

rotations = []
elements = [35, 15, 12, 22, 27, 20, 37]
root = None
for elem in elements:
    root = insert(root, elem)

leaves = find_leaves(root)
print("".join(map(str, leaves)), " ".join(rotations))
‘’’