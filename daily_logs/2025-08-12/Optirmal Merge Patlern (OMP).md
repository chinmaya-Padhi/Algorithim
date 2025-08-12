## Optimal Merge Pattern (OMP)
### Problem stmt : (Merging of File)
> Given a set of 'n' files (sorted) , it is req. to merge them into a single file , using 2 - way merging such that the no of record movement is minimum . 


```
record treenode {
    treenode *lchild;
    treenode *rchild;
    integer weight;
}
Procedure BUILD_TREE(list)
// list: a collection of n single-node trees (each node has a weight)
// After this, the procedure returns the root of the merged binary tree

1. while length(list) > 1 do
2.     left  := EXTRACT_MIN(list)    // remove node with smallest weight
3.     right := EXTRACT_MIN(list)    // remove node with next smallest weight
4.     parent := NEW_NODE()          // allocate a new internal node
5.     parent.lchild := left
6.     parent.rchild := right
7.     parent.weight := left.weight + right.weight
8.     INSERT(list, parent)          // put the merged node back into list
9. end while
10. return EXTRACT_MIN(list)         // the remaining node is the tree root


Start:  [2, 3, 8, 9, 15]

Step 1: Merge 2 & 3 → 5 → List: [5, 8, 9, 15]
Step 2: Merge 5 & 8 → 13 → List: [9, 13, 15]
Step 3: Merge 9 & 13 → 22 → List: [15, 22]
Step 4: Merge 15 & 22 → 37 (root)

| List Representation | Find Least | Insert   | Overall Complexity |
| ------------------- | ---------- | -------- | ------------------ |
| Linear List         | O(n)       | O(1)     | O(n²)              |
| Min-Heap            | O(log n)   | O(log n) | O(n log n)         |
