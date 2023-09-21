# leet-day68

# Rotate Linked List - LeetCode Problem

This C++ solution aims to solve the "Rotate Linked List" problem on LeetCode. Given a linked list, the task is to rotate it to the right by a given number of positions.

## Problem Statement

Given a linked list and an integer `k`, rotate the linked list to the right by `k` positions.

### Example

**Input:**
```
1 -> 2 -> 3 -> 4 -> 5
k = 2
```

**Output:**
```
4 -> 5 -> 1 -> 2 -> 3
```

## Approach and Algorithm

1. Check for base cases:
   - If the linked list is empty or has only one node, return the list as it is.
   
2. Calculate the length of the linked list by traversing it once.

3. Calculate the effective rotation count as `k % length`. If the effective rotation count is 0, return the list as it is since no rotation is needed.

4. Initialize pointers `end`, `ans`, and `last` to the head of the list. Move the `end` pointer `k` steps ahead.

5. Move `end` and the other two pointers (`ans` and `last`) simultaneously until `end` reaches the end of the list. This step effectively finds the new head of the rotated list (`ans`) and the last node of the original list (`last`).

6. Update the `next` pointers accordingly:
   - Set `end->next` to point to the original head, making the list circular.
   - Set `last->next` to NULL to break the circularity and form the final rotated list.
   
7. Return the `ans` pointer, which is the new head of the rotated list.

## Time Complexity

The algorithm traverses the linked list twice: once to calculate the length and once to find the new head and update the pointers. Therefore, the time complexity is O(N), where N is the number of nodes in the linked list.

## Space Complexity

The algorithm uses constant extra space for a few pointers, so the space complexity is O(1).

## How to Use

You can use this solution to rotate a linked list to the right by a specified number of positions. To use it, follow these steps:

1. Include the `ListNode` struct definition and the `rotateRight` function in your C++ code.

2. Create a linked list using the `ListNode` struct.

3. Call the `rotateRight` function with the head of your linked list and the desired number of positions to rotate.

4. The function will return the new head of the rotated linked list.

## Example Usage

```cpp
int main() {
    // Create a linked list, e.g., 1 -> 2 -> 3 -> 4 -> 5
    ListNode* head = new ListNode(1);
    head->next = new ListNode(2);
    head->next->next = new ListNode(3);
    head->next->next->next = new ListNode(4);
    head->next->next->next->next = new ListNode(5);

    // Rotate the linked list by 2 positions
    int k = 2;
    Solution solution;
    ListNode* rotatedHead = solution.rotateRight(head, k);

    // Print the rotated linked list
    while (rotatedHead != NULL) {
        std::cout << rotatedHead->val << " -> ";
        rotatedHead = rotatedHead->next;
    }
    std::cout << "nullptr" << std::endl;

    return 0;
}
