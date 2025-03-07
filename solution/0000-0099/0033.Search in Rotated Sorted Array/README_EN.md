# [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array)

[中文文档](/solution/0000-0099/0033.Search%20in%20Rotated%20Sorted%20Array/README.md)

## Description

<p>Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.</p>

<p>(i.e., <code>[0,1,2,4,5,6,7]</code> might become <code>[4,5,6,7,0,1,2]</code>).</p>

<p>You are given a target value to search. If found in the array return its index, otherwise return <code>-1</code>.</p>

<p>You may assume no duplicate exists in the array.</p>

<p>Your algorithm&#39;s runtime complexity must be in the order of&nbsp;<em>O</em>(log&nbsp;<em>n</em>).</p>

<p><strong>Example 1:</strong></p>

<pre>

<strong>Input:</strong> nums = [<code>4,5,6,7,0,1,2]</code>, target = 0

<strong>Output:</strong> 4

</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> nums = [<code>4,5,6,7,0,1,2]</code>, target = 3

<strong>Output:</strong> -1</pre>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            mid = (l + r) >> 1
            if nums[mid] == target:
                return mid
            if nums[mid] > target:
                if nums[mid] >= nums[r] and target < nums[l]:
                    l = mid + 1
                else:
                    r = mid - 1
            else:
                if nums[mid] <= nums[l] and target > nums[r]:
                    r = mid - 1
                else:
                    l = mid + 1
        return -1
```

### **Java**

```java
class Solution {
    public int search(int[] nums, int target) {
        int l = 0, r = nums.length - 1;
        while (l <= r) {
            int mid = (l + r) >>> 1;
            if (nums[mid] == target) return mid;
            if (nums[mid] > target) {
                if (nums[mid] >= nums[r] && target < nums[l]) l = mid + 1;
                else r = mid - 1;
            } else {
                if (nums[mid] <= nums[l] && target > nums[r]) r = mid - 1;
                else l = mid + 1;
            }
        }
        return -1;
    }
}
```

### **C++**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l = 0, r = nums.size() - 1;
        while (l <= r) {
            int mid = (l + r) >> 1;
            if (nums[mid] == target) return mid;
            if (nums[mid] > target) {
                if (nums[mid] >= nums[r] && target < nums[l]) l = mid + 1;
                else r = mid - 1;
            } else {
                if (nums[mid] <= nums[l] && target > nums[r]) r = mid - 1;
                else l = mid + 1;
            }
        }
        return -1;
    }
};
```

### **...**

```

```

<!-- tabs:end -->
