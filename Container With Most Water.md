

# LeetCode Problem: Container With Most Water

## Problem Description

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i`th line are `(i, 0)` and `(i, height[i])`.

Find two lines that, together with the x-axis, form a container that can store the **maximum amount of water**.

Return the **maximum area** of water the container can store.

---

### Examples

#### Example 1:

```plaintext
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The maximum area is between lines at index 1 and 8:
min(8, 7) * (8 - 1) = 7 * 7 = 49.
```

#### Example 2:

```plaintext
Input: height = [1,1]
Output: 1
Explanation: Only two lines available, so max area is 1 * (1 - 0) = 1.
```

---

### Constraints

* `n == height.length`
* `2 <= n <= 10^5`
* `0 <= height[i] <= 10^4`

---

## Solution

We use the **two-pointer** approach to calculate the maximum area by starting from both ends and moving inward, always moving the shorter line inward.

```java
class Solution {
    public static int maxArea(int[] height) {
        int area = 0, left = 0, right = height.length - 1;

        while (left < right) {
            int minHeight = Math.min(height[left], height[right]);
            area = Math.max(area, minHeight * (right - left));

            // Move the pointer pointing to the shorter line
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return area;
    }
}
```

---

## Complexity Analysis

### Time Complexity:

* **O(n)**: We iterate through the array once using two pointers.

### Space Complexity:

* **O(1)**: No extra space is used, only a few integer variables.

---

## Key Points

* Use the **two-pointer technique** for an optimal O(n) solution.
* The area is calculated as: `min(height[left], height[right]) * (right - left)`.
* Always move the pointer pointing to the shorter line to potentially find a taller one.

