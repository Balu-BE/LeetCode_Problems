

# LeetCode Problem: Longest Substring Without Repeating Characters

## Problem Description

Given a string `s`, find the length of the **longest substring** without repeating characters.

A *substring* is a contiguous sequence of characters within a string. Characters must not repeat in the substring.

### Examples

#### Example 1:

```plaintext
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

#### Example 2:

```plaintext
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

#### Example 3:

```plaintext
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
```

> Note: "pwke" is a subsequence, not a substring, so it doesn't count.

---

### Constraints

* `0 <= s.length <= 5 * 10^4`
* `s` consists of English letters, digits, symbols, and spaces.

---

## Solution

We use the **sliding window** technique with a `HashSet` to keep track of characters we've seen in the current window.

```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        int left = 0, right = 0, maxLength = 0;
        int len = s.length();
        
        while (right < len) {
            char c = s.charAt(right);
            
            // If character already exists in the set, remove from the left
            while (set.contains(c)) {
                set.remove(s.charAt(left));
                left++;
            }
            
            // Add current character and update max length
            set.add(c);
            maxLength = Math.max(maxLength, right - left + 1);
            right++;
        }
        
        return maxLength;
    }
}
```

---

## Complexity Analysis

### Time Complexity:

* **O(n)**: Each character is visited at most twice (once by `right`, once by `left`), so the overall time is linear with respect to the length of the string.

### Space Complexity:

* **O(min(n, m))**: We store characters in a `Set`, where `n` is the length of the string and `m` is the character set size (for English letters, digits, symbols, etc.).

This solution is efficient and optimal for large strings, thanks to the sliding window approach.


