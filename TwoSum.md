# LeetCode Problem: Two Sum

## Problem Description

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

### Examples

#### Example 1:
```plaintext
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

#### Example 2:
```plaintext
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

#### Example 3:
```plaintext
Input: nums = [3,3], target = 6
Output: [0,1]
```

### Constraints
- 2 <= nums.length <= 10^4
- -10^9 <= nums[i] <= 10^9
- -10^9 <= target <= 10^9
- Only one valid answer exists.

---

## Solution

```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int size = nums.length - 1;

        for (int i = 0; i <= size; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{-1, -1}; // In case no solution is found
    }
}
```

---

## Complexity Analysis

### Time Complexity:
- **O(n)**: The loop iterates through the array once, and each lookup and insertion in a hashmap takes constant time **O(1)**.

### Space Complexity:
- **O(n)**: The hashmap stores the numbers and their indices, with a maximum size of `n` elements.

This solution is optimal because it leverages the hashmap for efficient lookups, achieving linear time complexity compared to a potential quadratic time complexity using a brute-force approach.

