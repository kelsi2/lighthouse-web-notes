# Intro to Trees: Org charts

## Learning Outcomes
1. What are data structures
  * Arrays and objects === data structures
    * Data structures: Allow us to organize data to be managed more efficiently
  * Arrays good for lists, objects good for lookup by key
    * Most common data types and exist in most languages
2. What is a tree?
  * Tree is a common data structure
    * Think an org chart with CEO, supervisors, and employees
3. Why are trees useful?
  * Trees are about RELATIONSHIPS --> Easy to see how each piece of data is related
4. How to use a tree to organize data
  * Circle === Node: A key entity
    * Contains data about the entity
  * Connections between nodes === Edge
  * Top node === Root Node
  * Bottom nodes === Leaf Nodes
  * All nodes (except Root Node) have a Parent Node
  * All nodes (except Leaf Nodes) have 1+ Children Nodes
    * All child nodes with the same parents are siblings
  * Interesting side note: The DOM === TREE! :o
5. What is tree traversal?
  * Usually only have direct access to root node in the tree, not all nodes
    * Similar to array (only have reference to array itself, not all the elements in the array)
      * Use for loop for arrays, for trees this is known as TRAVERSING a tree
      * Similar to looping items in array, we visit all nodes in a tree
      * Can visit all nodes or just nodes under a specific node
6. Breadth first vs. depth first search
  * Breadth First:
    * Checks nodes closest to root node before checking nodes further away
      1. Root node
      2. Root's children
      3. Node's children
    * e.g.: access row by row until we find the thing we are looking for
  * Depth First:
    * Visits each node on a path all the way to the leaf node before visiting nodes on the next path
7. Use depth first search to search for an object in a tree
  * Tree is RECURSIVE data structure 
    * Made up of smaller sub trees, which are made up of smaller sub trees
      * Every node in the tree apart from the root is the root node of a smaller tree
      * Even a leaf node is the root node of a tree with 0 children
  * To traverse recursively:
    1. Visit root node
    2. Get first unvisited child sub-tree of the current node
    3. Do step 1 with sub-tree