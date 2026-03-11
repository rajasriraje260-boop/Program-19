class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key


def insert(root, key):
    if root is None:
        return Node(key)
    if key < root.val:
        root.left = insert(root.left, key)
    else:
        root.right = insert(root.right, key)
    return root


def search(root, key):
    if root is None or root.val == key:
        return root
    if key < root.val:
        return search(root.left, key)
    return search(root.right, key)


def minValueNode(node):
    current = node
    while current.left:
        current = current.left
    return current


def delete(root, key):
    if root is None:
        return root

    if key < root.val:
        root.left = delete(root.left, key)

    elif key > root.val:
        root.right = delete(root.right, key)

    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left

        temp = minValueNode(root.right)
        root.val = temp.val
        root.right = delete(root.right, temp.val)

    return root


def inorder(root):
    if root:
        inorder(root.left)
        print(root.val),
        inorder(root.right)


root = None
root = insert(root, 50)
insert(root, 30)
insert(root, 70)
insert(root, 20)
insert(root, 40)

print("BST elements:")
inorder(root)

print("\nSearching 40:")
if search(root, 40):
    print("Found")
else:
    print("Not Found")

root = delete(root, 20)
print("After deletion:")
inorder(root)# Program-19
Program 19
