# Lined List

## Common problem-solving methods or techniques

### 1.Dummy head node

When there's a need to handle the case where the pointer p is null, we can consider using a dummy head node, which can reduce the complexity of the code.

### 2.Fast and slow pointers

* When you need to process multiple linked lists at different speeds or conditions
* When you need to find a specific equidistant point in a linked list, you can use two pointers with proportional speeds. For example, finding the midpoint or detecting a cycle.

Leetcode 21, 86, 23, 876

### 3.Equidistant double pointers

* Finding the kth last node in a linked list
* Need to process data at equal distances

Leetcode 19

### 4.Recursion

```python
def traverse(head: ListNode):
    # Pre-order traversal code
    traverse(head.next)
    # Post-order traversal code
```

* When you need to process data from back to front, consider using recursion.

Leetcode 92, 206, 25

