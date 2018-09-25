# Technical Interview Cheat Sheet
_**Studying for a technical interview sucks, so here's a cheat sheet to help**_

_Credit to [TSiege](https://github.com/TSiege) for the original Gist, [found here](https://gist.github.com/TSiege/cbb0507082bb18ff7e4b) and [harrisonlingren](https://github.com/harrisonlingren) for the updated version_ 

This list is meant to be a both a quick guide and reference for further research into these topics.  It's basically a summary of that comp sci course you never took or forgot about, so there's no way it can cover everything in depth.

## Table of Contents
- [Data Structure Basics](#data-structure-basics)
  * [Array](#array)
  * [Linked List](#linked-list)
  * [Stack](#stack)
  * [Queue](#queue)
  * [Hash Table or Hash Map](#hash-table-or-hash-map)
  * [Binary Tree](#binary-tree)
- [Search Basics](#search-basics)
  * [Breadth First Search](#breadth-first-search)
  * [Depth First Search](#depth-first-search)
- [Efficient Sorting Basics](#efficient-sorting-basics)
  * [Merge Sort](#merge-sort)
  * [Quicksort](#quicksort)
  * [Bubble Sort](#bubble-sort)
- [Basic Types of Algorithms](#basic-types-of-algorithms)
  * [Recursive Algorithms](#recursive-algorithms)
  * [Iterative Algorithms](#iterative-algorithms)
  * [Greedy Algorithm](#greedy-algorithm)
- [Extra Reading](#extra-reading)

## Data Structure Basics

### Array
![Array](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/Array1.svg/320px-Array1.svg.png)
#### Definition:
- Stores data elements based on an sequential, most commonly 0 based, index.
- Based on [tuples](http://en.wikipedia.org/wiki/Tuple) from set theory.
- Any interview question involving an Array or a String could be asked using the other, use techniques from both.
  
#### What you need to know:
- Optimal for indexing; bad at searching, inserting, and deleting (except at the end).
- **Linear arrays**, or one dimensional arrays, are the most basic.
  - Are static in size, meaning that they are declared with a fixed size.
- **Dynamic arrays** are like one dimensional arrays, but have reserved space for additional elements.
  - If a dynamic array is full, it copies it's contents to a larger array. An O(n) operation.
- **Two dimensional arrays** have x and y indices like a grid or nested arrays, also called a Matrix.  
  
#### Big O efficiency:
- Indexing:         Linear array: O(1),      Dynamic array: O(1)
- Search:           Linear array: O(n),      Dynamic array: O(n)
- Optimized Search: Linear array: O(log n), Dynamic array: O(log n)
- Insertion:        Linear array: n/a        Dynamic array: O(n)
  

### Linked List
![Linked List](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/CPT-LinkedLists-addingnode.svg/474px-CPT-LinkedLists-addingnode.svg.png)
#### Definition: 
- Stores data with **nodes** that point to other nodes.
  - Nodes, at its most basic it has one datum and one reference (another node).
  - A linked list _chains_ nodes together by pointing one node's reference towards another node.
  - Common interview questions (find the middle) involve setting up more than 1 pointer and advancing them at different rates

#### What you need to know:
- Designed to optimize insertion and deletion, slow at indexing and searching.
- **Doubly linked list** has nodes that reference the previous node.
- **Circularly linked list** is simple linked list whose **tail**, the last node, references the **head**, the first node.

#### Big O efficiency:
- Indexing:         Linked Lists: O(n)
- Search:           Linked Lists: O(n)
- Optimized Search: Linked Lists: O(n)
- Insertion:        Linked Lists: O(1)  

### Stack
![Stack](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/320px-Data_stack.svg.png)
  - commonly implemented with linked lists but can be made from arrays too.
  - Stacks are **last in, first out** (LIFO) data structures.
  - When made with a linked list, the head is the only place for insertion and removal.
  - Big O depends on implementation
  
### Queue
![Queue](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Data_Queue.svg/320px-Data_Queue.svg.png)
  - Can be implemented with a linked list or an array.
  - Queues are a **first in, first out** (FIFO) data structure.
  - When made with a doubly linked list, only removes from head and adds to tail.  
  - Big O depends on implementation

### Hash Table or Hash Map
![Hash Table](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7d/Hash_table_3_1_1_0_1_0_0_SP.svg/320px-Hash_table_3_1_1_0_1_0_0_SP.svg.png)
#### Definition: 
- Stores data with key value pairs.
- **Hash functions** accept a key and return an output unique only to that specific key. 
  - This is known as **hashing**, which is the concept that an input and an output have a one-to-one correspondence to map information.
  - Hash functions return a unique id that is mapped to an index in an array via (id % array.length) to then store the data + the key

#### What you need to know:
- Designed to optimize searching, insertion, and deletion.
- **Hash collisions** are when a hash function returns the same output for two distinct inputs.
  - Most hash functions have this problem. 
  - This is often accommodated for by having the hash tables be very large and to pick a collision strategy
    - [Open Addressing](https://en.wikipedia.org/wiki/Open_addressing) will locate collisions in the closest adjacent open address (will need to store the key and probe to find later)
    - [Separate Chainging](https://en.wikipedia.org/wiki/Hash_table#Collision_resolution) creates buckets of linked lists to store elements with the same key, (will need to store the key and an O(n) search within that bucket to find later)
  - Some problems lend themselves to [perfect hashing](https://en.wikipedia.org/wiki/Perfect_hash_function) that won't require a large array or collision resolution. Usually things that are already unique and aren't very large (letters in the alphabet)
- Hashes are important for associative arrays and database indexing.

#### Big O efficiency:
- Indexing:         Hash Tables: O(1)
- Search:           Hash Tables: O(1)
- Insertion:        Hash Tables: O(1)  


### Binary Tree
![Non-Search Binary Tree](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Binary_tree_array_indices.svg/320px-Binary_tree_array_indices.svg.png)
#### Definition: 
- Is a tree like data structure where every node has at most two children, a left and a right.
- **Not all Binary Trees are Binary Search Trees! Clarify!**

#### What you need to know:
- Designed to optimize searching and sorting.
- A **degenerate tree** is an unbalanced tree, which if entirely one-sided is a essentially a linked list.
- Used to make **binary search trees**.
  - A binary tree that uses comparable keys to assign which direction a child is.
  - Left sub-tree (not just child) has all values smaller than its parent node.
  - Right sub-tree (not just child) has all values greater than its parent node.
  - Duplicates can pose problems, handle with storing the count along with the node or store all duplicates on the same side (right or left, just have to do it the same all the time) while still holding true to the requirement of larger right and smaller left sub trees
  - Binary Search trees are generally more usefull and not much more expensive to use and implment then regular binary trees so are generally more ubiquitous. 

#### Big O efficiency:
- Indexing:  Binary Search Tree: O(log n)
- Search:    Binary Search Tree: O(log n)
- Insertion: Binary Search Tree: O(log n) 


## Search Basics
### Breadth First Search
#### Definition:
- An algorithm that searches a tree (or graph) by searching levels of the tree first, starting at the root and moving down level by level

#### What you need to know:
- Optimal for searching a tree that is likely to have the answer near our head and/or has really long branches (even infinately long)
[xkcd DFS](https://xkcd.com/761/)
- Uses a queue to order the search when adding children to search 
- Because it uses a queue it is sometimes slightly more memory intensive than **depth first search** that uses a stack
 - pseudo code looks like this:
 ```
function BFS(targetValue) {
  queue = new queue();
  queue.add(root);
  while(!queue.isEmpty()) {
    currentNode = queue.dequeue();
    if (currentNode.getValue() == targetValue) {
      return true;
    }
    queue.addAll(currentNode.getChildren());
  }
  
  return false;
}
```  
  
#### Big O efficiency:
- Search: Breadth First Search: O(|E| + |V|)
- E is number of edges
- V is number of vertices

### Depth First Search
#### Definition:
- An algorithm that searches a tree (or graph) by searching depth of the tree first, starting at the root.
  - There are 3 orders, preorder (current, left, right), inorder (left, current, right) postorder (left, right, current)
  - It traverses down then entire sub-tree until it cannot go further before backtracking to continue in the order choosen.
  
#### What you need to know:
- Inorder used to print a binary tree in ascending order
- Uses a stack to push nodes onto to order the search so sometimes slightly less memory intensive than BFS.
 ```
function DFSPreOrder(targetValue) {
  stack = new stack();
  stack.push(root);
  while(!stack.isEmpty()) {
    currentNode = stack.pop();
    if (currentNode.getValue() == targetValue) {
      return true;
    }
    stack.add(currentNode.getRightChild());
    // left child will get popped first as it will be on top of our stack
    stack.add(currentNode.getLeftChild());
  }
  
  return false;
}
``` 
  
#### Big O efficiency:
- Search: Depth First Search: O(|E| + |V|)
- E is number of edges
- V is number of vertices


#### Breadth First Search Vs. Depth First Search
- The simple answer to this question is that it depends on the size and shape of the tree and where we expect the answer to be, but normally when just searching a binary tree, BFS is the safer route.
  - For wide, shallow trees, where answers tend to be close to our root use Breadth First Search
  - For deep, narrow trees, where answers usually involve searching the whole tree in a DFS given order, use Depth First Search

## Efficient Sorting Basics
### Merge Sort
#### Definition:
- A comparison based sorting algorithm
  - Divides entire dataset into groups of at most two.
  - Compares each number one at a time, moving the smallest number to left of the pair.
  - Once all pairs sorted it then compares left most elements of the two leftmost pairs creating a sorted group of four with the smallest numbers on the left and the largest ones on the right. 
  - This process is repeated until there is only one set.

#### What you need to know:
- This is one of the most basic sorting algorithms.
- Know that it divides all the data into as small possible sets then compares them.

#### Big O efficiency:
- Best Case Sort: Merge Sort: O(n log n)
- Average Case Sort: Merge Sort: O(n log n)
- Worst Case Sort: Merge Sort: O(n log n)

### Quicksort
#### Definition:
- A comparison based sorting algorithm
  - Divides entire dataset in half by selecting the average element and putting all smaller elements to the left of the average.
  - It repeats this process on the left side until it is comparing only two elements at which point the left side is sorted.
  - When the left side is finished sorting it performs the same operation on the right side.
- Computer architecture favors the quicksort process.

#### What you need to know:
- While it has the same Big O as (or worse in some cases) many other sorting algorithms it is often faster in practice than many other sorting algorithms, such as merge sort.
- Know that it halves the data set by the average continuously until all the information is sorted.

#### Big O efficiency:
- Best Case Sort: Quick Sort: O(n)
- Average Case Sort: Quick Sort: O(n log n)
- Worst Case Sort: Quick Sort: O(n^2)

### Bubble Sort
#### Definition:
- A comparison based sorting algorithm
  - It iterates left to right comparing every couplet, moving the smaller element to the left.
  - It repeats this process until it no longer moves and element to the left.

#### What you need to know:
- While it is very simple to implement, it is the least efficient of these three sorting methods.
- Know that it moves one space to the right comparing two elements at a time and moving the smaller on to left.

#### Big O efficiency:
- Best Case Sort: Merge Sort: O(n)
- Average Case Sort: Merge Sort: O(n^2)
- Worst Case Sort: Merge Sort: O(n^2)

#### Merge Sort Vs. Quicksort
- Quicksort is likely faster in practice.
- Merge Sort divides the set into the smallest possible groups immediately then reconstructs the incrementally as it sorts the groupings.
- Quicksort continually divides the set by the average, until the set is recursively sorted.

## Basic Types of Algorithms
### Recursive Algorithms
#### Definition:
- An algorithm that calls itself in its definition.
  - **Recursive case** a conditional statement that is used to trigger the recursion.
  - **Base case** a conditional statement that is used to break the recursion.

#### What you need to know:
- **Stack level too deep** and **stack overflow**.
  - If you've seen either of these from a recursive algorithm, you messed up.
  - It means that your base case was never triggered because it was faulty or the problem was so massive you ran out of RAM before reaching it.
  - Knowing whether or not you will reach a base case is integral to correctly using recursion.
  - Often used in Depth First Search


### Iterative Algorithms
#### Definition:
- An algorithm that is called repeatedly but for a finite number of times, each time being a single iteration.
  - Often used to move incrementally through a data set.

#### What you need to know:
- Generally you will see iteration as loops, for, while, and until statements.
- Think of iteration as moving one at a time through a set.
- Often used to move through an array.

#### Recursion Vs. Iteration
- The differences between recursion and iteration can be confusing to distinguish since both can be used to implement the other. But know that,
  - Recursion is, usually, more expressive and easier to implement.
  - Iteration uses less memory.
- **Functional languages** tend to use recursion. (i.e. Haskell)
- **Imperative languages** tend to use iteration. (i.e. Ruby)
- Check out this [Stack Overflow post](http://stackoverflow.com/questions/19794739/what-is-the-difference-between-iteration-and-recursion) for more info.

#### Pseudo Code of Moving Through an Array (this is why iteration is used for this)
```
Recursion                         | Iteration
----------------------------------|----------------------------------
recursive method (array, n)       | iterative method (array)
  if array[n] is not nil          |   for n from 0 to size of array
    print array[n]                |     print(array[n])
    recursive method(array, n+1)  |
  else                            |
    exit loop                     |
```
### Greedy Algorithm
#### Definition:
- An algorithm that, while executing, selects only the information that meets a certain criteria.
- The general five components, taken from [Wikipedia](http://en.wikipedia.org/wiki/Greedy_algorithm#Specifics):
  - A candidate set, from which a solution is created.
  - A selection function, which chooses the best candidate to be added to the solution.
  - A feasibility function, that is used to determine if a candidate can be used to contribute to a solution.
  - An objective function, which assigns a value to a solution, or a partial solution.
  - A solution function, which will indicate when we have discovered a complete solution.

#### What you need to know:
- Used to find the optimal solution for a given problem.
- Generally used on sets of data where only a small proportion of the information evaluated meets the desired result.
- Often a greedy algorithm can help reduce the Big O of an algorithm.

#### Pseudo Code of a Greedy Algorithm to Find Largest Difference of any Two Numbers in an Array.
```
greedy algorithm (array)
  var largest difference = 0
  var new difference = find next difference (array[n], array[n+1])
  largest difference = new difference if new difference is > largest difference
  repeat above two steps until all differences have been found
  return largest difference
```

This algorithm never needed to compare all the differences to one another, saving it an entire iteration.

## Extra Reading
* [Ace the Coding Interview Every Time](https://medium.com/@nickciubotariu/ace-the-coding-interview-every-time-d169ce1fd3fc)
