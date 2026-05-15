# 🚀 Day 25 – Product of Array Except Self

## 📌 Problem

Given an integer array `nums`, return an array `answer` such that:

```python
answer[i]
```

is equal to the product of all elements of `nums` except `nums[i]`.

You must solve it:

* without using division
* in `O(n)` time

### Example

```python
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

---

# 💡 Approach – Prefix Product + Suffix Product

Instead of calculating the product separately for every index (`O(n²)`),
we use:

* prefix products
* suffix products

### Key Idea

For every index:

```python
answer[i] = prefix_product * suffix_product
```

Where:

* `prefix_product` = product of all elements before `i`
* `suffix_product` = product of all elements after `i`

---

# ⚙️ Python Solution

```python
class Solution:
    def productExceptSelf(self, nums):
        n = len(nums)
        answer = [1] * n

        prefix = 1
        for i in range(n):
            answer[i] = prefix
            prefix *= nums[i]

        suffix = 1
        for i in range(n - 1, -1, -1):
            answer[i] *= suffix
            suffix *= nums[i]

        return answer
```

---

# 🧠 Dry Run

Input:

```python
nums = [1,2,3,4]
```

### Prefix Pass

| Index | Prefix | Answer    |
| ----- | ------ | --------- |
| 0     | 1      | [1,1,1,1] |
| 1     | 1      | [1,1,1,1] |
| 2     | 2      | [1,1,2,1] |
| 3     | 6      | [1,1,2,6] |

### Suffix Pass

| Index | Suffix | Answer      |
| ----- | ------ | ----------- |
| 3     | 1      | [1,1,2,6]   |
| 2     | 4      | [1,1,8,6]   |
| 1     | 12     | [1,12,8,6]  |
| 0     | 24     | [24,12,8,6] |

Final Answer:

```python
[24,12,8,6]
```

---

# ⏱️ Complexity Analysis

| Complexity       | Value            |
| ---------------- | ---------------- |
| Time Complexity  | O(n)             |
| Space Complexity | O(1) extra space |

---

# 🧠 Key Learning

This problem teaches:

* Prefix and suffix computation
* Space optimization
* Efficient array transformation

Prefix-suffix patterns are extremely important in array-based interview problems.

---

# ⚠️ Important Insight

Division is avoided because:

* arrays may contain zeros
* division-based solutions can fail edge cases

Using prefix and suffix products handles all cases safely.

---

# 🔗 LeetCode

Product of Array Except Self – LeetCode #238

---

# 📈 Progress Log

✅ Day 25 of DSA Journey
