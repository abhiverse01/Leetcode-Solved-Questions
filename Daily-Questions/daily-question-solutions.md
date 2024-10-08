# Daily LeetCode Problems/ Solutions

- This document contains the solutions to LeetCode problems solved today, detailed explanations and the final solutions.


---

## Summary
- **Problem 1**: We found the minimum number of swaps needed to balance a string of brackets. The solution runs in \( O(n) \) time and space.
- **Problem 2**: We transformed a string into a fancy string by deleting the minimum number of characters, ensuring that no three consecutive characters are the same. This solution also runs in \( O(n) \) time and space.


---

## Problem 1: Minimum Swaps to Make a String Balanced

### Question
You are given a 0-indexed string `s` of even length `n`. The string consists of exactly `n / 2` opening brackets `'['` and `n / 2` closing brackets `']'`.

A string is called balanced if and only if:
- It is the empty string, or
- It can be written as AB, where both A and B are balanced strings, or
- It can be written as `[C]`, where C is a balanced string.

You may swap the brackets at any two indices any number of times. Return the minimum number of swaps to make `s` balanced.

### Examples
1. **Input**: `s = "][]["`
   - **Output**: `1`
   - **Explanation**: You can make the string balanced by swapping index `0` with index `3`. The resulting string is `[[]]`.

2. **Input**: `s = "]]][[["`
   - **Output**: `2`
   - **Explanation**: Swap index `0` with index `4`, then swap index `1` with index `5`. The resulting string is `[[][]]`.

3. **Input**: `s = "[]"` 
   - **Output**: `0`
   - **Explanation**: The string is already balanced.

### Solution

```python
class Solution(object):
    def minSwaps(self, s):
        """
        :type s: str
        :rtype: int
        """
        balance = 0
        swaps = 0
        
        for char in s:
            if char == '[':
                balance += 1
            else:
                balance -= 1
            
            # If balance goes negative, we have more closing brackets
            # than opening brackets in the prefix, and we need a swap.
            if balance < 0:
                swaps += 1
                # Reset balance by imagining we swap a '[' to fix this imbalance
                balance = 1
        
        return swaps
```

### Explanation
This solution uses a counter (`balance`) to track the balance of brackets. When it goes negative, it indicates an imbalance requiring a swap. We keep track of these imbalances and count the necessary swaps to balance the string efficiently.

---

## Problem 2: Make Fancy String

### Question
A fancy string is a string where no three consecutive characters are equal.

Given a string `s`, delete the minimum possible number of characters from `s` to make it fancy.

Return the final string after the deletion. It can be shown that the answer will always be unique.

### Examples
1. **Input**: `s = "leeetcode"`
   - **Output**: `"leetcode"`
   - **Explanation**: Remove an `'e'` from the first group of `'e'`s to create `"leetcode"`. No three consecutive characters are equal, so return `"leetcode"`.

2. **Input**: `s = "aaabaaaa"`
   - **Output**: `"aabaa"`
   - **Explanation**: Remove characters to create `"aabaa"`, ensuring no three consecutive characters are the same.

3. **Input**: `s = "aab"`
   - **Output**: `"aab"`
   - **Explanation**: The string is already fancy.

### Solution

```python
class Solution(object):
    def makeFancyString(self, s):
        """
        :type s: str
        :rtype: str
        """
        # Convert string to a list to easily modify it
        result = [s[0]]  # Start with the first character
        
        # Iterate from the second character to the end
        for i in range(1, len(s)):
            # Add character only if it doesn't form three consecutive identical characters
            if len(result) >= 2 and s[i] == result[-1] == result[-2]:
                continue  # Skip adding this character
            result.append(s[i])
        
        # Join the list back into a string
        return "".join(result)
```

### Explanation
The solution iterates through the string and builds a result list while ensuring that no three consecutive characters are the same. By checking the last two characters in the list, we efficiently decide whether to add the current character.



