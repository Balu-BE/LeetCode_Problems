

# LeetCode Problem: Palindrome Number

## Problem Description

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

An integer is a palindrome when it reads the same **backward** as **forward**.

---

### Examples

#### Example 1:

```plaintext
Input: x = 121
Output: true
Explanation: 121 reads the same from left to right and right to left.
```

#### Example 2:

```plaintext
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-.
```

#### Example 3:

```plaintext
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Not the same as 10.
```

---

### Constraints

* `-2^31 <= x <= 2^31 - 1`

---

## Solution

We reverse the digits of the number and compare the result with the original number. We skip negative numbers immediately since they cannot be palindromes.

```java
class Solution {
    public boolean isPalindrome(int x) {
        // Negative numbers are not palindromes
        if (x < 0) return false;

        int copy = x;
        int rev = 0;

        while (x > 0) {
            rev = rev * 10 + x % 10;
            x = x / 10;
        }

        return copy == rev;
    }
}
```

---

## Complexity Analysis

### Time Complexity:

* **O(log₁₀(n))**: The number of digits in `x` determines the number of iterations.

### Space Complexity:

* **O(1)**: Only a constant amount of space is used for variables.

---

## Key Points

* Negative numbers are **never** palindromes.
* Reversal is done digit-by-digit using modulo and division.
* No need to convert to a string, which improves efficiency.

