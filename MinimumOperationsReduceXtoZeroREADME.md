# leet-day68

# Minimum Operations to Reduce X to Zero

## Problem Description

You are given an integer array `nums` and an integer `x`. In one operation, you can either remove the leftmost or the rightmost element from the array `nums` and subtract its value from `x`. The goal is to find the minimum number of operations required to reduce `x` to exactly 0 if it is possible, otherwise return -1.

### Example 1

Input: 
```cpp
nums = [1,1,4,2,3], x = 5
```

Output: 
```
2
```

Explanation: The optimal solution is to remove the last two elements to reduce `x` to zero.

### Example 2

Input: 
```cpp
nums = [5,6,7,8,9], x = 4
```

Output: 
```
-1
```

### Example 3

Input: 
```cpp
nums = [3,2,20,1,1,3], x = 10
```

Output: 
```
5
```

Explanation: The optimal solution is to remove the last three elements and the first two elements (5 operations in total) to reduce `x` to zero.

## Approach

To solve this problem, we can think in reverse. Instead of finding the minimum prefix + suffix, we can find the maximum subarray. Finding the maximum subarray is a standard problem and can be done greedily.

1. Calculate the `target` as the sum of all elements in the `nums` array minus `x`.

2. If `target` is equal to 0, return the length of the `nums` array, as we can remove all elements to reach the target.

3. Initialize a `prefixSum` hash map with a key of 0 at index -1.

4. Initialize `maxLength` to -1.

5. Iterate through the `nums` array and calculate the current prefix sum.

6. Check if `currentSum - target` exists in the `prefixSum` hash map. If it does, calculate the length of the subarray with the target sum and update `maxLength`.

7. Store the current prefix sum in the `prefixSum` hash map with its index.

8. Finally, return `n - maxLength` as the minimum number of operations, where `n` is the length of the original array.

## Usage

You can use the provided C++ code to solve this problem. Here's how to use the `Solution` class:

```cpp
#include <vector>

class Solution {
public:
    int minOperations(std::vector<int>& nums, int x);
};

int main() {
    Solution solution;
    std::vector<int> nums = {1,1,4,2,3};
    int x = 5;
    int result = solution.minOperations(nums, x);
    // Print or use the result as needed.
    return 0;
}
```

Replace `nums` and `x` with your input, and then call the `minOperations` function to get the minimum number of operations.

