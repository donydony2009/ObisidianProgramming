- Producing a **cummulative array** can be done in O(n) by first counting the occurences and then summing them
- Finding a **majority** or even who took more than a third of votes can be done with **Boyer–Moore majority vote algorithm** (essentially count++ if it's majority count-- otherwise and all the votes will eliminate each others until only the majority is left)

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