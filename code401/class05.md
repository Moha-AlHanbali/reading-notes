[Home](README.md)

<br>

# Linked Lists

<br>

## Readings from [Big O: Analysis of Algorithm Efficiency](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/big_oh.html)

<br>

- Key Areas for Big O analysis:
  - Input Size
  - Units of Measurement
  - Orders of Growth
  - Best Case, Worst Case, and Average Case

<br>

### Input Size

<br>

> Input Size refers to the size of the parameter values that are read by the algorithm.

> This does not simply refer to the number of parameters an algorithm reads, but takes into account the size of each parameter value as well.

> The higher the  Input Size `n`, the more likely there will be an increase to Running Time and Memory Space.

<br>

### Units of Measurement

<br>

- To quantify the Running Time in our analysis, we will consider Three Measurements of time:
  - The time in milliseconds from the start of a function execution until it ends.
  - The number of operations that are executed.
  - The number of “Basic Operations” that are executed (the operation that is contributing the most to the total running time).

<br>

- To quantify Memory Space, we can consider Four Sources of Memory Usage during function run-time:
  - The amount of space needed to hold the code for the algorithm.
  - The amount of space needed to hold the input data.
  - The amount of space needed for the output data.
  - The amount of space needed to hold working space during the calculation (This will also include Stack Space of recursive function calls … specifically how memory usage scales relatively with the size of the input.).

<br>

  > Space Complexity and Time Complexity are measured differently and should be analyzed separately.

<br>

### Orders of Growth

<br>

> As the value of n grows, the Order of Growth represents the increase in Running Time or Memory Space.

<br>

![OrdersOfGrowth.png](/imgs/OrdersOfGrowth.png)

<br>

### Constant Complexity `O(1)`

<br>

![ConstantEfficiency.png](/imgs/ConstantEfficiency.png)

<br>

> Means that no matter what inputs are thrown at our algorithm, it always uses the same amount of time or space. The number 1 is used to represent a constant value. The actual number of units will most likely be greater than 1, we round this number down to 1 to represent our estimate of complexity that is independant of n.

<br>

### Logarithmic Complexity `O(lgn)`

<br>

![LogarithmicEfficiency.png](/imgs/LogarithmicEfficiency.png)

<br>

> Represents a function that sees a decrease in the rate of complexity growth, the greater our value of n. This can be seen when we are performing calculations on sorted data. For instance if we are searching for a value in a sorted array, we have an idea of where to start searching instead of starting at the first index moving toward n.

<br>

### Linear Complexity `O(n)`

<br>

![LinearEfficiency.png](/imgs/LinearEfficiency.png)

<br>

> If an algorithm has Linear Complexity, the size of our inputs ‘n’ will directly determine the amount of Memory Space used and Running Time length. This is a very common efficiency and is usually used to denote functions with loops, or often algorithms that use recursion.

<br>

### Summary

<br>

![EfficiencyNotations.png](/imgs/EfficiencyNotations.png)

<br>

<br>

## Readings from [Linked Lists](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/singly_linked_list.html)

<br>

> A Linked List is a sequence of Nodes that are connected/linked to each other. The most defining feature of a Linked List is that each Node references the next Node in the link.

<br>

- There are two types of Linked List:
 - Singly
   - A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list.
 - Doubly
   - A Doubly linked list means that there is a reference to both the Next and Previous node.

<br>

> Nodes are the individual items/links that live in a linked list. Each node contains the data for each link.

<br>

> Each node contains a property called Next. This property contains the reference to the next node.

<br>

> The Head is a reference of type Node to the first node in a linked list.

<br>

> The Current is a reference of type Node to the node that is currently being looked at. When traversing, you create a new Current variable at the Head to guarantee you are starting from the beginning of the linked list.

<br>

### Traversal

<br>

> When traversing a linked list, you are not able to use a foreach or for loop.

> We depend on the Next value in each node to guide us where the next reference is pointing.

> The Next property is exceptionally important because it will lead us where the next node is and allow us to extract the data appropriately.

<br>

> The best way to approach a traversal is through the use of a while() loop. 

> This allows us to continually check that the Next node in the list is not null. 

> If we accidentally end up trying to traverse on a node that is null, a NullReferenceException gets thrown and our program will crash/end.

<br>

> When traversing through a linked list, the Current variable will tell us where exactly in the linked list we are and will allow us to move/traverse forward until we hit the end.

<br>

### Traversal Big O

<br>

> The Big O of time for Includes would be `O(n)`. 

> This is because, at its worse case, the node we are looking for will be the very last node in the linked list. 

> `n` represents the number of nodes in the linked list.

<br>

> The Big O of space for Includes would be `O(1)`. 

> This is because there is no additional space being used than what is already given to us with the linked list input.

<br>

### Adding a Node

<br>

> If we want to add a node with an `O(1)` efficiency, we have to replace the current Head of the linked list with the new node, without losing the reference to the next node in the list.

> Regardless of the number of Nodes that this linked list has, it will always be a `O(1)` time and space because it takes the same amount of time to add a new node to the beginning of the list, and no additional resources are being used.

<br>

> Adding a node to the middle of a linked list is a bit different than adding to the beginning. This is because we are working with more nodes and must re-allocate to make room for the new node.

> The time efficiency of this transaction would be `O(n)` because we could be inserting the new node, worst case scenario, at the end. With n being the number of nodes possible, we would therefore have `O(n)` time efficiency.

> Space efficiency would stay at an `O(1)` because, like before, no additional space is being used allocated outside of what is given to us on the input.

<br>

### Prerequisites

<br>

> When making your Node class, consider requiring a value to be passed in to require that each node has a value

<br>


## Readings from [What’s a Linked List, Anyway [Part 1]](https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d) and [What’s a Linked List, Anyway? [Part 2]](https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996)

<br>

### Linear data structures

<br>

> One characteristic of linked lists is that they are linear data structures, which means that there is a sequence and an order to how they are constructed and traversed.

> In order to get to the end of the list, we have to go through all of the items in the list in order, or sequentially. 

>  In non-linear data structures, items don’t have to be arranged in order, which means that we could traverse the data structure non-sequentially.

<br>

### Memory management

<br>

> The biggest differentiator between arrays and linked lists is the way that they use memory in our machines.

> When an array is created, it needs a certain amount of memory. If we had 7 letters that we needed to store in an array, we would need 7 bytes of memory to represent that array.

> But, we’d need all of that memory in one contiguous block. That is to say, our computer would need to locate 7 bytes of memory that was free, one byte next to the another, all together, in one place.

> On the other hand, when a linked list is born, it doesn’t need 7 bytes of memory all in one place. One byte could live somewhere, while the next byte could be stored in another place in memory altogether! 

> Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.

<br>

> The fundamental difference between arrays and linked lists is that arrays are static data structures, while linked lists are dynamic data structures.

> A static data structure needs all of its resources to be allocated when the structure is created; this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory. 

> If more elements needed to be added to a static data structure and it didn’t have enough memory, you’d need to copy the data of that array, for example, and recreate it with more memory, so that you could add elements to it.

<br>

> On the other hand, a dynamic data structure can shrink and grow in memory. It doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape can change, and the amount of memory it needs can change as well.

<br>

### Parts of a linked list

<br>

>  A linked list is made up of a series of nodes, which are the elements of the list.

> The starting point of the list is a reference to the first node, which is referred to as the head.

> Nearly all linked lists must have a head, because this is effectively the only entry point to the list and all of its elements, and without it, you wouldn’t know where to start! 

> The end of the list isn’t a node, but rather a node that points to null, or an empty value.

<br>

> A single node is also pretty simple. It has just two parts: data, or the information that the node contains, and a reference to the next node.

> A single node doesn’t know how long the linked list is, and it may not necessarily even know where it starts, or where it ends.

<br>

### Lists for all shapes and sizes

<br>

> Singly linked lists are the simplest type of linked list, based solely on the fact that they only go in one direction.

> There is a single track that we can traverse the list in; we start at the head node, and traverse from the root until the last node, which will end at an empty null value.

<br>

> A node can reference its subsequent neighbor node, it can also have a reference pointer to its preceding node, too!

> This is what we call a doubly linked list, because there are two references contained within each node: a reference to the next node, as well as the previous node.

> This can be helpful if we wanted to be able to traverse our data structure not just in a single track or direction, but also backwards, too.

<br>

> A circular linked list is a little odd in that it doesn’t end with a node pointing to a null value.

> Instead, it has a node that acts as the tail of the list (rather than the conventional head node), and the node after the tail node is the beginning of the list. 

<br>

### What even is the Big O?

<br>

>  Big O Notation is a way of evaluating the performance of an algorithm.

> Big O notation is a way to express the amount of time that a function, action, or algorithm takes to run based on how many elements we pass to that function.

<br>

> There are a ton of different equations used to define the space and time complexity of an algorithm, and most of them involve an O (referred to as just “O” or sometimes as “order”), and a variable n, where n is the size of the input (think back to our our ten, thousands, or millions of numbers).

<br>

> An `O(1)` function takes constant time, which is to say that it doesn’t matter how many elements we have, or how huge our input is: it’ll always take the same amount of time and memory to run our algorithm.

> An `O(n)` function is linear, which means that as our input grows (from ten numbers, to ten thousand, to ten million), the space and time that we need to run that algorithm grows linearly.

> `O(n²)` function, which clearly takes exponentially more time and memory the more elements that you have. 

<br>

### Growing a linked list

<br>

> All we really need to do is rearrange our pointers. We know that a linked list is made up a single node, and a node always contains some data and, most importantly, a pointer to the next node or null. So, all we need to do in order to add something to our linked list is figure out which pointer needs to point to where.

<br>

> Inserting an element at the beginning of a linked list is particularly nice and efficient because it takes the same amount of time, no matter how long our list is, which is to say it has a space time complexity that is constant, or `O(1)`.

<br>

### To list or not to list

<br>

> A linked list is usually efficient when it comes to adding and removing most elements, but can be very slow to search and find a single element.

<br>

> If you ever find yourself having to do something that requires a lot of traversal, iteration, or quick index-level access, a linked list could be your worst enemy. 

>In those situations, an array might be a better solution.

> If you find yourself wanting to add a bunch of elements to a list and aren’t worried about finding elements again later, or if you know that you won’t need to traverse through the entirety of the list, a linked list could be your new best friend.

