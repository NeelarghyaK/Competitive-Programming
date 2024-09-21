****Binary Search Trees**** - A binary tree where each node has at most two children, and for every node, all values in the left subtree are smaller, and all values in the right subtree are larger. In the worst case, an unbalanced BST can become a linked list with O(n) time complexity for search, insert, and delete.
![image](https://github.com/user-attachments/assets/372bbce4-2681-4935-bc64-c6ae7bbbdceb)
![image](https://github.com/user-attachments/assets/e8742b19-ffba-4ed9-b547-5201765373dc)
![image](https://github.com/user-attachments/assets/39735f75-ed1a-4244-9241-1f5a3385aab4)

To print out the elements in sorted order, perform inorder traversal(i.e., Left--parent--right).






****Self-Balancing Binary Trees:****

These trees maintain a balanced structure to ensure O(log n) time complexity for search, insert, and delete operations.

**-> Red-Black Tree**
_Description:_ A self-balancing BST where each node has an additional "color" (red or black). The tree uses a set of balancing rules involving these colors to ensure that the longest path from root to leaf is at most twice as long as the shortest.

_Properties:_
No two consecutive red nodes.
The root and leaves (null nodes) are black.
Red-Black Trees have O(log n) height.
Every simple path from a node to a descendant leaf contains the same number of black nodes.
_Use:_ Typically used in C++ STL (std::set, std::map) and Java's TreeMap
