# Integrating ChatGPT
* Is it a collaborator?
* Is it a teacher?
* Is it a mirror?

## Goals
* Can it speed learning?
  * Are the highest values productivity, replicability, standardization?
* Can it deepen learning?
  * Are the highest values craftsmanship, depth, quality, originality?
* How does it change the mentor/mentee relationship?
  * An info source: Show/Explain something
  * an info sink: Verify an explanation
* How does it change the job of programming?
  * Outcomes
    * Similar to the situation when the Berlin Wall fell
      * The young could adapt
      * Older folks could not
    * How does this apply to programming

* Methodology
  * Using it to write code
  * Using it to explain concepts
  * Mentor is watching over-the-shoulder
    * directing how it is used

* Initial results
  * Used to explore/learn the pairing heap data structures
  * Gave the "standard" pairing heap code
  * There is a "bottom" there - Was repetitive
  * Some Wrong Results

## Self-Adjusting Binary Search Trees

### Advantages
1. Always nearly as efficient as constrained structures and often much better
2. Consume less space because they do not store constraint metadata
3. Access and update algorithms are simple

### Potential Disadvantages
1. Require more local adjustments, especially during accesses
2. Individual operations within a sequence can be expensive, which may be a drawback in realtime system

### Vocabulary
- Amortized time - time per operation averaged over a worst-case sequence of operations
- Minimum priority queue - The next value in the queue has the minimum priority
- Maximum priority queue - The next element is the maximum priority
- Pairing Heap - {{data,priority}, [heaps]} - Its a recursive structure {{7,7},[{{9,9}[]}, {{10,10},[]},...]}
  - Heap is ordered by priority
  - Has the same performance for storing elements as a perfectly balanced tree
    - Removal - O(log n)
    - Addition - 01
  - Meld - merging 2 heaps left to right
    - meld(meld(heap1, heap2), meld_pairs(tail_heaps))
  - Unwind meld pairs left to right

### Efficiency 
- Balanced trees [height-balanced, weight-balanced, B-tree] have a worst-case time bound of O(log n) per operation on an n-node tree
  - Insertion and deletion cost is very high
  - Higher cost due to structural constraints
- Biased search trees - Trade fast average access time of optimum trees with the fast updating time of balanced trees with more complicated structural constraints and higher maintain costs than balanced trees 
- $\theta$ 

## Going Deeper
* Logic Programming - Prolog
* Look up indexes in C - offset