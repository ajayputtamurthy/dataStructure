To find the height of a binary tree in Java, you can use a recursive approach. The height of a tree is defined as the number of edges on the longest path from the root to a leaf node. Here is a Java implementation to find the height of a binary tree:

### Node Class Definition

First, define a class for the nodes of the tree:

```java
class Node {
    int data;
    Node left, right;

    public Node(int item) {
        data = item;
        left = right = null;
    }
}
```

### BinaryTree Class Definition

Next, define the `BinaryTree` class with a method to find the height:

```java
public class BinaryTree {
    Node root;

    // Method to find the height of the binary tree
    int height(Node node) {
        if (node == null) {
            return -1; // Return -1 for height in case of null to count edges
        } else {
            // Compute the height of each subtree
            int leftHeight = height(node.left);
            int rightHeight = height(node.right);

            // Use the larger one
            return Math.max(leftHeight, rightHeight) + 1;
        }
    }

    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // Creating a sample tree:
        //        1
        //       / \
        //      2   3
        //     / \
        //    4   5

        tree.root = new Node(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);

        System.out.println("The height of the binary tree is: " + tree.height(tree.root));
    }
}
```

### Explanation

1. **Node Class:**
   ```java
   class Node {
       int data;
       Node left, right;

       public Node(int item) {
           data = item;
           left = right = null;
       }
   }
   ```
   This class represents each node in the binary tree, where `data` is the value stored in the node, and `left` and `right` are references to the left and right child nodes, respectively.

2. **BinaryTree Class:**
   ```java
   public class BinaryTree {
       Node root;
   ```
   The `BinaryTree` class contains a reference to the root node of the tree.

3. **Height Method:**
   ```java
   int height(Node node) {
       if (node == null) {
           return -1; // Return -1 to count edges
       } else {
           int leftHeight = height(node.left);
           int rightHeight = height(node.right);
           return Math.max(leftHeight, rightHeight) + 1;
       }
   }
   ```
   - This method computes the height of a subtree rooted at the given node.
   - If the node is `null`, it returns `-1`, which counts the number of edges rather than the number of nodes. If you want to count nodes, change the return value to `0`.
   - It recursively computes the height of the left and right subtrees and returns the maximum of the two heights plus one.

4. **Main Method:**
   ```java
   public static void main(String[] args) {
       BinaryTree tree = new BinaryTree();
       tree.root = new Node(1);
       tree.root.left = new Node(2);
       tree.root.right = new Node(3);
       tree.root.left.left = new Node(4);
       tree.root.left.right = new Node(5);

       System.out.println("The height of the binary tree is: " + tree.height(tree.root));
   }
   ```
   - This sets up a sample binary tree and calls the `height` method on the root node to print the height of the tree.

When you run this code, the output will be:
```
The height of the binary tree is: 2
```

This result indicates that the longest path from the root to a leaf node has 2 edges.