- Producing a **cummulative array** can be done in O(n) by first counting the occurences and then summing them
- Finding a **majority** or even who took more than a third of votes can be done with **Boyer–Moore majority vote algorithm** (essentially count++ if it's majority count-- otherwise and all the votes will eliminate each others until only the majority is left. You can think of it as each majority vote kills another vote. At the end  only the majority will survive. Can be used to count top 2 as well)

### Arrays
### Rotate
To rotate an array you can do 3 reversals.
Rotate means 
k = 3
1 2 3 4 5 6 7
5 6 7 1 2 3 4

One way to rotate it is:
1. Reverse whole array
2. Reverse 0 - k
3. Reverse k - end
Ex:
k = 3
1 2 3 4 5 6 7
**7 6 5 4 3 2 1**
**5 6 7** 4 3 2 1
5 6 7 **1 2 3 4**

### Sorted Array
- 1 index parsing
- 2 index parsing
- Binary search

#### Binary Tree
- Closes element to the current node is either the rightmost node of the left child or  the leftmost node of the right child

### DP
- You can use a tail to track the path of the DP. In this case `tail[i]` will hold the ith step. Additionally tail it can sometimes be binary_searched.

### Heap 
- Min heap: std::make_heap(v1.begin(), v1.end(), [std::greater](http://en.cppreference.com/w/cpp/utility/functional/greater)<>{});
- Hint: k different things?
- Hint2: Continuous push pop max.