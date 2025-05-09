# 🏛️ LeetCode Problem 13: Roman to Integer

## ✅ Problem Description

Roman numerals are represented by seven symbols:

| Symbol | Value |
| ------ | ----- |
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

Some special cases use **subtraction**:

* I before V or X → 4 (IV), 9 (IX)
* X before L or C → 40 (XL), 90 (XC)
* C before D or M → 400 (CD), 900 (CM)

### 🧠 Task

Given a valid Roman numeral `s`, return its **integer** value.

---

## 💡 Examples

### Example 1:

```plaintext
Input: s = "III"
Output: 3
Explanation: III = 1 + 1 + 1 = 3
```

### Example 2:

```plaintext
Input: s = "LVIII"
Output: 58
Explanation: L = 50, V = 5, III = 3
```

### Example 3:

```plaintext
Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90, IV = 4
```

---

## ✅ Constraints

* `1 <= s.length <= 15`
* `s` contains only Roman numeral characters: `I, V, X, L, C, D, M`
* Valid input in range \[1, 3999]

---

## ✅ Java Code Solution

```java
class Solution {
    public int romanToInt(String s) {
        String roman = "IVXLCDM";
        int[] num = {1, 5, 10, 50, 100, 500, 1000};

        Map<Character, Integer> romanMap = new HashMap<>();

        // Map Roman symbols to values
        for (int i = 0; i < num.length; i++) {
            romanMap.put(roman.charAt(i), num[i]);
        }

        int n = s.length();
        int ans = romanMap.get(s.charAt(n - 1)); // Start from last symbol

        // Traverse from right to left (excluding last char already handled)
        for (int i = n - 2; i >= 0; i--) {
            int current = romanMap.get(s.charAt(i));
            int next = romanMap.get(s.charAt(i + 1));

            if (current < next) {
                ans -= current; // Subtract in case of special condition
            } else {
                ans += current;
            }
        }

        return ans;
    }
}
```

---

## 📈 Time & Space Complexity

* **Time Complexity:** `O(n)` — where `n` is the length of the Roman numeral string
* **Space Complexity:** `O(1)` — constant space for the map and variables

---

## 🧪 Dry Run: Input = "MCMXCIV"

```
s = "M C M X C I V"
val=1000 100 1000 10 100 1 5

From right to left:
V(5) > I(1): add 5
I(1) < C(100): subtract 1 → total = 4
C(100) > X(10): add 100 → total = 94
X(10) < M(1000): subtract 10 → total = 84
M(1000) > C(100): add 1000 → total = 1084
C(100) < M(1000): subtract 100 → total = 984
M(1000): add 1000 → total = 1984

✅ Final answer: 1994
```

---

## ✅ Key Takeaways

* Use a **map** to store Roman-to-integer values.
* Check whether current value is **less than** next → **subtract** it.
* Else, **add** it.

