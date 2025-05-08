

# LeetCode Problem: Reverse Integer

## Problem Description

Given a signed 32-bit integer `x`, return `x` with its digits reversed.

If the reversed integer overflows the 32-bit signed integer range `[-2^31, 2^31 - 1]`, return `0`.

> **Note:** You are not allowed to use 64-bit integers in your solution.

---

### Examples

#### Example 1:

```plaintext
Input: x = 123
Output: 321
```

#### Example 2:

```plaintext
Input: x = -123
Output: -321
```

#### Example 3:

```plaintext
Input: x = 120
Output: 21
```

---

### Constraints

* `-2^31 <= x <= 2^31 - 1`
* No usage of 64-bit integers

---

## Solution

We reverse the digits one-by-one using modulo and division. Before adding the digit to the result, we **check for overflow**.

```java
class Solution {
    public int reverse(int x) {
        int ans = 0;

        while (x != 0) {
            int digit = x % 10;

            // Check for overflow before multiplying by 10
            if (ans > Integer.MAX_VALUE / 10 || ans < Integer.MIN_VALUE / 10) {
                return 0;
            }

            ans = ans * 10 + digit;
            x /= 10;
        }

        return ans;
    }
}
```

---

## Complexity Analysis

### Time Complexity:

* **O(log₁₀(n))**: The number of digits in the integer determines the number of loop iterations.

### Space Complexity:

* **O(1)**: Only a constant amount of variables are used.

---

## Key Points

* We avoid using 64-bit types like `long`.
* We **check for overflow** *before* multiplying `ans` by 10.
* This solution safely handles both positive and negative integers.

