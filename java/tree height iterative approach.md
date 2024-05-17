To find the height of a binary tree iteratively, you can use a level-order traversal (BFS) approach with the help of a queue. This method traverses the tree level by level and counts the levels to determine the height.

Here's how you can implement this in Java:

### Node Class Definition

First, define the `Node` class for the tree nodes:

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

### BinaryTree Class with Iterative Height Method

Next, define the `BinaryTree` class with an iterative method to find the height:

```java
import java.util.LinkedList;
import java.util.Queue;

public class BinaryTree {
    Node root;

    // Iterative method to find the height of the binary tree
    int height() {
        if (root == null) {
            return -1; // Return -1 to count edges
        }

        Queue<Node> queue = new LinkedList<>();
        queue.add(root);
        int height = -1;

        while (!queue.isEmpty()) {
            int nodeCount = queue.size();
            height++;

            while (nodeCount > 0) {
                Node node = queue.poll();
                if (node.left != null) {
                    queue.add(node.left);
                }
                if (node.right != null) {
                    queue.add(node.right);
                }
                nodeCount--;
            }
        }

        return height;
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

        System.out.println("The height of the binary tree is: " + tree.height());
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
   This class represents each node in the binary tree.

2. **BinaryTree Class:**
   ```java
   public class BinaryTree {
       Node root;
   ```
   The `BinaryTree` class contains a reference to the root node of the tree.

3. **Iterative Height Method:**
   ```java
   int height() {
       if (root == null) {
           return -1; // Return -1 to count edges
       }

       Queue<Node> queue = new LinkedList<>();
       queue.add(root);
       int height = -1;

       while (!queue.isEmpty()) {
           int nodeCount = queue.size();
           height++;

           while (nodeCount > 0) {
               Node node = queue.poll();
               if (node.left != null) {
                   queue.add(node.left);
               }
               if (node.right != null) {
                   queue.add(node.right);
               }
               nodeCount--;
           }
       }

       return height;
   }
   ```
   - This method uses a queue to perform a level-order traversal of the tree.
   - It initializes the queue with the root node.
   - The outer `while` loop runs as long as there are nodes in the queue.
   - The inner `while` loop processes all nodes at the current level and enqueues their non-null children.
   - The height variable is incremented at each level to keep track of the tree's height.

4. **Main Method:**
   ```java
   public static void main(String[] args) {
       BinaryTree tree = new BinaryTree();
       tree.root = new Node(1);
       tree.root.left = new Node(2);
       tree.root.right = new Node(3);
       tree.root.left.left = new Node(4);
       tree.root.left.right = new Node(5);

       System.out.println("The height of the binary tree is: " + tree.height());
   }
   ```
   - This sets up a sample binary tree and calls the `height` method to print the height of the tree.

When you run this code, the output will be:
```
The height of the binary tree is: 2
```

This result indicates that the longest path from the root to a leaf node has 2 edges.