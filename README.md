#  <img src="https://cloud.githubusercontent.com/assets/7833470/10899314/63829980-8188-11e5-8cdd-4ded5bcb6e36.png" height="60">  Trees!

## Objectives:
- List the tree vocabulary words
- Identify the Big(O) value of search using binary search trees  
- Describe the breadth first 
- Create an implementation of a breadth first search
- Create an implementation of a depth first search

## Trees
Trees are one of the big ideas in search and are somewhat unique conceptually so their common interview questions for 
developers. 

## Basic Vocabulary 

- **Node** or **Vertex** A place to store data. Usually we have a key and some additional data in a node.
- **Edge** A connection between two nodes. It can represent an association or relationship between nodes. An edge can be undirected or directed.  
- **Graph** A combination of vertices and edges. Graphs are often modeled as node and edge objects or as a matrix where the 
rows and columns represent the nodes and the values of the matrix represent the edges. 
- **Tree** A special graph where there is a root node and each node other than the root has only one parent. The node without a parent is called the root node. The other other nodes are called leaves.
- **Binary Search Tree** A tree where each node has 2 children. The node to the left is less than the 
parent. The node to the right is bigger than the parent.
- A **Balanced Tree** means that all of the nodes of given height are filled in before the next height is started. A balanced tree will have the smallest height possible given the number of nodes in a tree.
- *Trie** A specialized tree to organize word lists. Each node is a letter. There may also be a special node called the ``end`` node that stores the end of a word. Edges exist between two nodes if there is a word were the child letter follows the parent. Tries make things like autocomplete easier to complete.

A fact that 

### Some pictures
A graph 

<img src="images/graph-terms.png" width="350px">


A tree

<img src="images/tree-terms.png" width="300px">


A binary search tree

<img src="images/bst-example.png" width="300px">

A trie

<img src="images/trie-example.png" width="400px" alt="trie storing on, one, tan, tap, tar, two">


# Breadth First

Breadth First Search is an algorithm for searching through graphs, looking for one or more nodes that meet some search criteria. Breadth first ordering can also be used to traverse a graph, that is, to visit all of its nodes.

When searching for a particular key in a binary search tree, we can take advantage of the fact that each node's left subtree contains smaller keys and each node's right subtree contains larger keys. Breadth First Search is more general -- it doesn't make any assumptions about the relationships among nodes' keys. In fact, we can search by criteria that aren't based on keys at all. 

**Breadth First Search chooses a start node and "visits" every node of a graph in order of how many edges the node is from that start.**  In a tree, we pick the root as the start node. We'll also consider each node to be the same "length." In graph terms, that means the "weight" of each edge is the same. Breadth first search only works for graphs with unweighted edges or graphs where all the edge weights are the same.

Breadth First Search spreads across the tree or graph like mold on bread, moving outward one step at a time from its start location.  The algorithm keeps track of which nodes to process with a queue, since it wants to process the nodes in the order it encountered them.  Pay attention to the order nodes are turning black in the animation below.   

<img src="https://upload.wikimedia.org/wikipedia/commons/4/46/Animated_BFS.gif" alt="breadth first search animation for tree" width="300px">

What's happening in that animation?   

```
node queue starts out with just root:
	[a]
enqueue first item's (unvisited) children; dequeue first item:
	[b, c]			=> a
enqueue first item's children; dequeue first item:
	[c, d, e]		=> b
enqueue first item's children; dequeue first item:
	[d, e, f, g]	=> c
enqueue first item's children (none!); dequeue first item:
	[e, f, g]		=> d
keep repeating until the queue is empty:
	[f, g, h]		=> e
	[g, h]			=> f
	[h]				=> g
	[]				=> h
```


## Exercises: Breadth First Tree Search

1. In English, describe how you would use breadth first search to find any node with a given key. Your algorithm should assume you have a tree data structure and that you can access each node's key and its array of children. (Do not assume it's a binary search tree.) You should also assume you're given a target key to match.

1. On the whiteboard, pseudocode a breadth first search function. Assume you have a tree data structure that allows the following operations:

	* given a tree/node `my_tree`, get the root of the tree with `my_tree`
	* given a tree/node, get the key of the node with `.key`
	* given a tree/node, get the children of the node with `.children`


# Depth First 

Depth First Search is another algorithm that searches through (potentially) every node in a graph. Like with Breadth First Search, we can search for many keys, search by criteria that aren't based on keys, keep track of depth. Also like with breadth first, we can use the depth first order to traverse an entire tree even if we aren't searching for something.

**Depth First Search chooses a start node and "visits" all the nodes in the graph by following each path as far (as deep) as it can before going to the next path.**  In a tree, we pick the root as the start node (surprise!).

Depth First Search follows an "always go left" path like some people use to systematically solve mazes. 

Breadth First Search used a queue (first in is first out) to keep track of which nodes to visit next.  Depth First Search, at least in its iterative form, uses a stack (first in is last out).

Depth First Search can also be done recursively. However, the iterative version translates more easily to graphs that might have loops (after you see both versions, think about why that is).


<img src="https://upload.wikimedia.org/wikipedia/commons/7/7f/Depth-First-Search.gif" alt="depth first search animation for tree" width="300px">

What's happening in that animation?

```
node stack starts with just the root:  
	[1]
visit the last node, pushing its children to the stack (added right to left to match gif but either works): 
	[1, 9, 5, 2]  
visit the last node, pushing its children to the stack:
	[1, 9, 5, 2, 3]
visit the last node, pushing its children to the stack:
	[1, 9, 5, 2, 3, 4]
visit the last node, but it has no unvisited children. so pop it out
	[1, 9, 5, 2, 3] 	=> 4
keep repeating until the stack is empty: 
	[1, 9, 5, 2]  		=> 3
	[1, 9, 5]  			=> 2
	[1, 9, 5, 8, 6]
	[1, 9, 5, 8]  		=> 6
	[1, 9, 5]			=> 8
	[1, 9]				=> 5
	[1, 9, 10]
	[1, 9]				=> 10
	[1] 				=> 9
	[]					=> 1
```


## Exercises: Depth First Tree Search

1. In English, describe how you would use depth first search to determine whether any node in a tree has a given key. Your algorithm should assume you have a tree data structure and that you can access each node's key its array of children. (Do not assume it's a binary search tree.) You should also assume you're given a target key to match.


1. On the whiteboard, pseudocode a depth first search function. As usual, assume you have a tree data structure that allows the following operations:
	
	* given a tree/node `my_tree`, get the root of the tree with `my_tree`
	* given a tree/node, get the key of the node with `.key`
	* given a tree/node, get the children of the node with `.children`

# Independent Work 

In the ``breadth_first_search.rb`` file, implement the breadth first search. At each step in the process you should print out 
to the console the search queue so we can see you are using the breadth first search. The file has sample output but don't 
worry if you're output doesn't match exactly.

In the ``depth_first_search.rb`` file, implement the depth first search. As each step in the process you should print out the 
current search stack so we can see you are using the depth first search. The file has sample output but don't worry if you're 
output doesn't match exactly.

# Bonus 

Work through the ``tree-practice/vocab-practice-with-solutions.md`` file. This file is a great tree refresher for interviews.


Featured contents of this repository:

[quick-reference.md](quick-reference.md) - a brief summary of tree types, operations, and traversal

[tree-practice/](tree-practice) - practice tasks for general trees, binary search trees, and tries

[longer-reference.md](longer-reference.md) - a longer set of notes including run times and interview tips 

## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
