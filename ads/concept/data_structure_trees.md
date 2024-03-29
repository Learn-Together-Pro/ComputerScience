# :chart_with_upwards_trend: Data Structure : Trees Concepts

##### Tries

- B-Tree
- AVL Tree
- Red Black Tree
- Heap Tree
- Cartesian Tree
- Treap
- Splay Tree
- Tries Tree
- Ternary Tree
- Suffix Tree

##### Complete Binary Tree

A binary tree is complete if all levels except possibly the last are completely filled, and all nodes are as left as possible.

In other words, if you think of it as an array representation, there are no missing elements in the array except for the last level, where the missing elements are all on the right side.

##### Complete Binary Tree Types

- Almost Complete Binary Tree
- Perfect Binary Tree

##### Almost Complete Binary Tree

This term is often used interchangeably with a complete binary tree, and it follows the same rules: all levels except possibly the last are completely filled, and the last level has all its nodes as left as possible.

##### Perfect Binary Tree

A perfect binary tree is a type of binary tree in which every internal node has exactly two children, and all the leaf nodes are at the same level.

Every level of the tree is fully filled, so it is both complete and full.
In a perfect binary tree of height h, there will be exactly 2h−1 nodes.

##### B-Tree

A B-tree is a self-balancing tree data structure that maintains sorted data in a way that allows searches, sequential access, insertions, and deletions to be performed efficiently. Several invariants (properties that the tree maintains at all times) define a valid B-tree:

##### B-Tree Complexity

- Search: O(log⁡n) - In the worst case, searching for an element requires traversing from the root node to a leaf node.
- Insertion: O(log⁡n) - Inserting a new key may require splitting nodes, but the tree's balanced nature ensures this is done in logarithmic time.
- Deletion: O(log⁡n) - Deletion can also involve merging or redistributing keys, but again this can be done in logarithmic time.

##### B-Tree Invariants

- Root Node: If the tree is non-empty, it has a root node, even if it contains only one key.
- All Leaves at the Same Level: All the leaf nodes (external nodes) must be at the same depth, i.e., all paths from the root to the leaf nodes have the same length.
- Non-Root Node Key/Children Count: Every internal node (excluding the root) must contain at least m/2 keys where m is the maximum number of keys that a node can hold. Likewise, it must have at least m/2 + 1 children.
- Root Node Key/Children Count: The root node must have at least one key if it's not a leaf. If the root is a leaf, it can have zero keys. In terms of children, the root must have at least two children if it's not a leaf.
- Maximum Keys in Node: Every node can contain at most m keys.
- Node Fullness: Every node (except the root) must be at least half full.
- Sorted Keys: The keys within a node are sorted in non-decreasing order.
- Child Node Key Range: For a given node with keys k1, k2, ..., kn, the keys in the i-th child node (for i = 0 to n) must be greater than ki-1 and less than or equal to ki.
- Leaf Node Level: All leaves appear in the same level, and carry no information.
- Sequential Pointers in Leaves: If the B-tree is used as a B+-tree, all leaves may contain a pointer to the next leaf, forming a linked list of leaves for efficient sequential access.

##### AVL Tree

An AVL (Adelson-Velsky and Landis) tree is a self-balancing binary search tree in which the balance factor of every node must be in the specific range.

##### AVL Tree Invariants

- Binary Search Tree Property: An AVL tree must be a valid binary search tree (BST). This means that for any given node, the keys in its left subtree must be less than the key in the node, and the keys in its right subtree must be greater than the key in the node.
- Balance Factor: The balance factor of a node in an AVL tree is the height of its left subtree minus the height of its right subtree. The balance factor of every node must be in the range of -1 to 1, inclusive. This means:
  - A balance factor of 0 indicates that the left and right subtrees have the same height.
  - A balance factor of 1 indicates that the left subtree is one level deeper than the right subtree.
  - A balance factor of -1 indicates that the right subtree is one level deeper than the left subtree.
- Height-Balance Property: The tree must be "height-balanced," meaning that for every node in the tree, the heights of its two child subtrees differ by at most 1. This is a direct result of the balance factor constraint.
- Rebalancing After Operations: After performing an insertion or deletion operation, the tree must be rebalanced if necessary to restore the height-balance property. This is typically done using rotations (single or double rotations).
- Subtree Property: Every subtree of an AVL tree must also be an AVL tree. This ensures that the AVL property is maintained throughout the entire tree, not just at the top levels.
- Height Calculation: The height of a node is 1 plus the maximum of the heights of its left and right children. By convention, the height of an empty subtree (null pointer) is considered to be -1.
- Order Property: The in-order traversal of an AVL tree must produce the keys in ascending sorted order. This is a consequence of the binary search tree property.

##### Red Black Tree

Red-Black Trees are a type of binary search tree with additional properties that ensure the tree remains approximately balanced, guaranteeing O(log⁡n) time complexity for standard operations.

##### Red Black Tree Invariants

- Node Color: Every node is colored, either red or black.
- Root Property: The root of the tree is always black.
- Red Node Property: No two consecutive red nodes can be adjacent; i.e., the children of every red node must be black (and thus no red node can have a red parent). This prevents the formation of long sequences of red nodes, which could unbalance the tree.
- Black Height Property: Every simple path from a given node to any of its descendant leaves must have the same black depth (the number of black nodes). This property ensures that the tree remains approximately balanced.
- New Insertions: Newly inserted nodes are always red. If this leads to violation of the red node property, re-coloring and rotation are done to restore the properties.
- Leaf Nodes: Leaves (null pointers) are considered black.
- Binary Search Tree Property: A Red-Black Tree must satisfy all the properties of a binary search tree (BST), meaning the left subtree of every node contains only nodes with keys less than the node's key, and the right subtree only nodes with keys greater than the node's key.
- Black Depth: The black depth of a node is defined as the number of black nodes from the root to that node. This property helps maintain a balanced structure by ensuring that paths from the root to any leaf have the same number of black nodes.
- Rebalancing After Operations: Like AVL trees, Red-Black Trees may require rebalancing (rotations and re-coloring) after insertions and deletions to maintain the invariants.
- Order Property: The in-order traversal of a Red-Black Tree must produce the keys in ascending sorted order.

##### AVL vs Red Black Tree

- AVL is more balanced than Red Black Tree what costs performance on insertions and deletions.
- If the primary concern is lookup time and you're doing more searches compared to insertions and deletions, an AVL tree might be preferable.
- If you need a good balance of search, insert, and delete times, especially if insertions and deletions are common, a Red-Black tree might be a better choice.
- If memory is a significant concern, the reduced storage requirements of a Red-Black tree might make it preferable over an AVL tree.

##### Heap Tree

A heap is a special tree-based data structure that satisfies the heap property.

It is an important structure because it's efficient for priority queue operations, such as insertion, maximum extraction, and sorting. There are two types of heaps: max-heaps and min-heaps.

##### Heap Tree Invariants

- Heap Order Property: For any given node II, value(I)≥value(J) for all children J of node I.
- Complete Binary Tree: Every level, except possibly the last, is completely filled, and all nodes are as left as possible.
- Structural Property: A max-heap must be a complete binary tree, meaning all levels of the tree are fully filled except possibly for the last level, which is filled from left to right.

##### Binomial Heap

A binomial heap is a collection of binomial trees where each binomial tree follows the heap property, and there is at most one binomial tree of each degree.

Binominal heap is extension of binary heap.

##### Binomial Heap Invariants

- The root list property: The root list of a binomial heap is a list of all the trees in the heap, in decreasing order of tree size.
- The degree property: The degree of a tree in a binomial heap is at most 1.
- The root list merging property: If two trees with the same degree are merged, then the resulting tree has degree 2.
- The minimum property: The root list of a binomial heap always contains a tree with the minimum key value.

##### Binomial Heap Complexity

- **Structure**: Strict, enforced by binomial trees.
- **Insertion**: O(log n).
- **Merging**: O(log n).
- **Decrease Key**: O(log n).
- **Delete Min**: O(log n).

##### Binominal Heap as Array

```rust
fn parent( i : usize ) -> usize
{
  ( i - 1 ) / 2
}

fn left_child( i : usize ) -> usize
{
  2 * i + 1
}

fn right_child( i : usize ) -> usize
{
  2 * i + 2
}

fn number_of_node( height : usize ) -> usize
{
  2_usize.pow( height as u32 ) - 1
}

fn height_of_tree( nnodes : usize ) -> u32
{
  nnodes.ilog( 2 )
}

fn branches_range( nnodes : usize ) -> ( usize, usize )
{
  ( 0, nnodes / 2 - 1 )
}

fn leaves_range( nnodes : usize ) -> ( usize, usize )
{
  ( nnodes / 2, nnodes - 1 )
}

```

##### Leftist Heap

A leftist heap or leftist tree is a type of binary heap that satisfies the heap property and where the null path length (the shortest path from a node to a descendant leaf) of the left child is always greater or equal to that of the right child.

#### Leftist Heap Invariants

- The leftist property: for every node `x`, the size of the left subtree of `x` is at least as large as the size of the right subtree of `x`.
- The rank property: the rank of a node `x` is the length of the longest path from `x` to a leaf in the leftist heap.
- The null path length property: for every node `x`, the null path length of `x` is equal to the rank of `x` minus 1.

##### Leftist Heap Complexity

- **Structure**: Binary heap with added balancing condition.
- **Insertion**: O(log n).
- **Merging**: O(log n).
- **Decrease Key**: O(log n).
- **Delete Min**: O(log n).

##### Fibonacci Heap

A Fibonacci heap is a collection of marked unordered trees where no constraints are enforced on the child and sibling pointers.

##### Fibonacci Heap Invariants

- The **root list property:** The root list of a Fibonacci heap is a doubly linked list of all the nodes in the heap, in decreasing order of key value.
- The **degree property:** No node in a Fibonacci heap has more than two children.
- The **marked property:** At most one node in a Fibonacci heap can be marked at any given time.
- The **fibonacci heap property:** The children of a marked node form a Fibonacci heap.

##### Fibonacci Heap Complexity

- **Structure**: Flexible, no strict rules for child and sibling pointers.
- **Insertion**: O(1) amortized.
- **Merging**: O(1) amortized.
- **Decrease Key**: O(1) amortized.
- **Delete Min**: O(log n) amortized.

##### Cartesian Tree

A Cartesian tree is a binary tree derived from a sequence of numbers, constructed in a way that maintains both the binary search tree property and the heap property.

In the binary search tree property, all values in the left subtree of a node are less than the value of the node, and all values in the right subtree are greater. In the heap property, the value of a node is less than or equal to the values of its children (in a min-heap) or greater than or equal to them (in a max-heap). The Cartesian tree is unique for a given sequence of distinct numbers, and its in-order traversal yields the original sequence.

##### Cartesian Tree Invariants

- Binary Search Tree (BST) Property: The keys in a Cartesian tree follow the BST property. For any given node, all keys in its left subtree are less than the key in the node, and all keys in its right subtree are greater than the key in the node.
- Heap Property: The value at any given node (often based on some attribute like the original index in the array from which the tree was constructed) is less (or greater, depending on whether it's a min- or max-heap) than the values of its children.
- In-Order Traversal: An in-order traversal of the keys in a Cartesian tree yields the original sequence from which the tree was constructed. This is a unique feature that distinguishes Cartesian trees from other types of trees.
- Uniqueness: For a given sequence of distinct keys, there is exactly one Cartesian tree that can be constructed. This invariant ensures that the structure is well-defined.
- No Duplicate Keys: While this is not a strict requirement, most Cartesian trees are defined for sequences of distinct keys. If duplicate keys are allowed, additional rules must be defined to handle them.

##### Cartesian Tree Application

Cartesian trees are useful when you need a data structure that maintains the original sequence's structure while also being heap-ordered. They are particularly prominent in range query problems, computational geometry, and certain string processing tasks. Their unique properties make them suitable for various algorithms and applications where both ordering and heap characteristics are required.

- Range Minimum Queries (RMQs): Cartesian trees are widely used to answer RMQs, which find the minimum value in a given subarray of an array. The Cartesian tree helps perform these queries efficiently.
- Maintaining Order Statistics: When there's a need to maintain the order statistics of a dataset with insertions and deletions, Cartesian trees can be handy.
- Histogram Algorithms: Cartesian trees are used in algorithms to find the largest rectangular area in a histogram, a common problem in computational geometry.
- Building Treap Data Structure: Cartesian trees are an essential component in the construction of the treap data structure (a randomized binary search tree), which combines the properties of heaps and binary search trees.
- Converting Inorder Traversal: When you need to convert an inorder traversal of a binary tree along with another traversal (such as preorder), a Cartesian tree can be useful in reconstructing the original binary tree.
- Used in Suffix Trees: Cartesian trees play a role in the construction of suffix trees, a crucial data structure in string processing and pattern matching.
- Divide and Conquer Algorithms: Cartesian trees are useful in certain divide and conquer algorithms where you need to split the problem based on specific criteria related to the original sequence's structure.
- Spatial Data Structures: In computational geometry, Cartesian trees can be applied to spatial data structures and multidimensional searching problems.
- Merging Heaps: Cartesian trees provide a mechanism to efficiently merge two max-heaps or two min-heaps.

##### Treap

A treap is a data structure that combines the properties of a binary search tree (BST) and a binary heap.

It's named "treap" as a portmanteau of "tree" and "heap."

Like a binary search tree, the treap maintains an ordering among the keys such that the in-order traversal of the treap returns the keys in sorted order. Like a heap, each node also carries a priority, and the parent's priority must be higher (for a max-heap) or lower (for a min-heap) than the priorities of its children.

The treap is constructed by using randomized priority values, which helps to ensure that the tree remains approximately balanced, with logarithmic height. This gives the operations like insertion, deletion, and lookup expected average time complexities of O(logn), making it an efficient data structure.

##### Treap Invariants

- Binary Search Tree (BST) Invariant:
  - All nodes in the left subtree of a node have keys less than the key of the node.
  - All nodes in the right subtree of a node have keys greater than the key of the node.
  - The left and right subtrees of a node are also binary search trees.
  - No duplicate keys are allowed.
- Heap Invariant (Priority Invariant):
  - Each node has an associated priority value.
  - The priority of a node is greater than or equal to the priorities of its children (in a max-heap structure).
  - Priorities are usually randomly generated to maintain the balance of the tree.

##### Treap Applications

Treaps can be a compelling choice when you want the benefits of a balanced binary search tree but prefer a more straightforward implementation, or when the unique combination of BST and heap properties aligns with your particular use case.

- Simplicity of Implementation: Treaps are often easier to implement compared to other balanced binary search trees. This can make them a suitable choice for situations where simplicity and development speed are important.
- Ordered Operations: If you need to perform ordered operations like finding the kth smallest or largest element, a treap can do this efficiently.
- Dynamic Sets: When you need to maintain a dynamic set with frequent insertions and deletions, and you want to keep the set ordered, treaps can be an effective solution.
- Range Queries: Treaps allow for efficient range queries, insertions, and deletions, making them suitable for applications where these operations are common.
- In Cases Where Heaps Aren't Suitable: Sometimes, you might start with a heap but realize that you need to perform ordered operations that heaps aren't good at. A treap can give you the heap-like behavior along with the ordered operations of a binary search tree.
- Avoiding Worst-Case Scenarios: In applications where the data might be adversarial (causing a BST to degrade into a linked list), the randomness in treap might be advantageous.
- Versatility in Programming Contests: Treaps are a popular choice in competitive programming because of their relatively simple implementation and the combination of features from both heaps and BSTs.
- Memory Efficiency: Since they don't require storing balance factors or color (as in AVL or Red-Black trees), treaps might be a more memory-efficient option for maintaining a balanced binary search tree.
- Specialized Use Cases: Some specific applications might benefit from the combined heap and binary search tree properties, such as certain types of geometric algorithms or instances where both priority and order must be maintained.

##### Cartesian Tree vs Treap

A treap and a Cartesian tree are related data structures but are not exactly the same. They both combine properties of binary search trees (BST) and heaps, but they are used in different contexts and have different properties.

A treap is a type of randomized Cartesian tree. When you add random priorities to the nodes in a specific sequence, the resulting Cartesian tree is a treap. Thus, you can view the treap as a specialized version of the Cartesian tree, where the randomization helps achieve balance.

While the treap and Cartesian tree share similarities in combining the properties of BSTs and heaps, they are distinct in construction and purpose. Treaps use random priorities to maintain balance, while Cartesian trees are constructed directly from a given sequence without randomization.

##### Splay Tree

A splay tree is a self-adjusting binary search tree with the additional property that recently accessed elements are quick to access again.

It performs basic operations such as insertion, deletion, and lookup in O(log⁡n) amortized time, where n is the number of elements in the tree.

Unlike other balanced trees such as AVL or Red-Black trees, splay trees do not require adherence to strict balancing criteria. Instead, they reorganize themselves with each access (insertion, deletion, or lookup), so that the element accessed is moved to the root of the tree.

##### Splay Tree Invariants

- Binary Search Tree Property: A splay tree is a binary search tree. For any given node II, the values of the left subtree are less than II, and the values of the right subtree are greater than II.
- Self-Adjusting: After accessing a node (whether for insertion, deletion, or lookup), the tree reorganizes itself to move the accessed node to the root. This is done using a splaying operation, which consists of a series of rotations.
- Amortized Time Complexity: Though individual operations can take as long as O(n) time in the worst case, the amortized time complexity for insertions, deletions, and lookups is O(log⁡n).

##### Tries Tree ~ Prefix Tree

A Trie, also known as a prefix tree or digital tree, is a tree-like data structure that stores a dynamic set of strings, where the keys are usually strings.

Tries are used primarily for searching among a set of string keys. Tries are particularly useful for applications that require efficient search, insertion, and deletion operations on strings, such as implementing dictionaries, autocomplete features, spell checkers, and so forth.

##### Tries Tree

- Root Node: The root node represents an empty string or a common prefix for all the strings.
- Edges and Nodes: Each edge in the trie represents a character of a string. A node in a trie has as many edges as the number of characters in the alphabet.
- String Concatenation from Root: The concatenation of the characters along a path from the root to any node spells a string (or a prefix of a string) in the trie.
- Common Prefix: Any two strings with a common prefix share a common ancestor node that represents that prefix. The deeper the node, the longer the shared prefix.
- End of String Marker: There is a need to mark the end of a string, either by using a special end-of-string character or a specific flag or value in the node.
- Children's Characters: All children of a node have different characters associated with the edges leading to them.
- Space Complexity: A trie can have up to ALPHABET_SIZE×NALPHABET_SIZE×N nodes, where N is the number of keys, and ALPHABET_SIZEALPHABET_SIZE is the size of the alphabet.
Search Complexity: The search operation in a trie takes O(M) time, where MM is the length of the key to be searched.

##### Ternary Tree

A Ternary Search Tree (TST) is a specialized data structure used mainly for string handling and is a type of trie.

It's a hybrid between a binary search tree and a trie. Ternary search trees combine some of the best properties of both binary search trees and tries. They can be used for various string processing tasks, such as building a dictionary of words, auto-complete suggestions, etc. Like tries, they provide efficient search and retrieval, but like binary search trees, they don't need to store all possible characters at each level, leading to potential space savings.

##### Ternary Search Tree Invariants

- Three-way branching: Each node in a TST has three children: left, middle, and right.
Key Order Invariant:
  - The left subtree of a node contains keys that are less than the key of the node.
  - The right subtree of a node contains keys that are greater than the key of the node.
  - The middle subtree of a node continues with the next character of the key or keys that are equal in the current character comparison.
- End of String Marker: There must be some way to mark the end of a string. This is often done with a special value or flag in the node that corresponds to the last character of the string.
- Null Links: Links that do not correspond to characters will be null. This can make the TST more space-efficient compared to a standard trie.
- Character Storage: Each node contains a character, and a string is represented by the characters on a path from the root to a marked node representing the end of the string.

##### Suffix Tree

Compressed trie containing all the suffixes of a given string.

It is a powerful data structure used in various string operations like pattern matching. Here are some of its invariants and properties:

##### Suffix Tree Invariants

- Total Suffixes: The tree contains all possible suffixes of the given string. If the string has n characters, there will be n leaf nodes, each representing a unique suffix.
- Edge Labeling: Each edge is labeled with a non-empty substring of the input string. No two edges out of a node can have edge labels begining with the same character.
- Path Labeling: The concatenation of edge labels on the path from the root to a leaf represents the corresponding suffix of the string.
- Suffix Links: (Optional but often included) For internal nodes representing the string y (where y is a non-empty substring of the input string), there may be a suffix link to another internal node representing the suffix of y (i.e., y without its first character).
- Uniqueness of Internal Nodes: Every internal node, other than the root, must have at least two children. This helps in the compression of the trie into a tree structure.
- Leaf Labels: The leaves are often labeled with the start indices of the suffixes in the original string. This allows for efficient pattern matching and other operations.
- Single String Representation: A Suffix Tree is typically built for a single input string. If used for multiple strings, a unique termination symbol must be appended to each string to ensure that no string is a prefix of another.

##### Fenwick Tree ~ Binary Indexed Tree ~ BIT

The *Fenwick Tree*, also known as *Binary Indexed Tree (BIT)*, is a data structure that provides efficient methods for performing prefix sums (cumulative sums) on an array of numbers.

It's especially beneficial for arrays that are frequently updated. The Fenwick Tree strikes a balance between the raw speed of array-based structures and the dynamic properties of tree-based structures. Its logarithmic operation time makes it a valuable tool for specific problems where both updates to the data and cumulative queries are frequent.

##### Fenwick Tree : Time Complexity

- *Query (Prefix Sum)*: `O(log n)`
- *Update*: `O(log n)`

##### Fenwick Tree : Application

- *Dynamic Cumulative Sums*: If you need to maintain a dynamic list of numbers where you frequently update the numbers and query the cumulative sum, a Fenwick Tree offers a balance between update and query efficiency.
- *Range Sum Queries*: With slight modifications, it can be used for range sum queries, where you want to find out the sum of numbers between any two indices quickly.
- *Inversion Count in an Array*: Fenwick Tree can be employed to count the number of inversions in an array more efficiently than using a simple nested loop approach.
- *Implementing Advanced Data Structures*: It can be used to implement more advanced data structures like order-statistic trees.
