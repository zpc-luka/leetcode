# [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs)

[中文文档](/solution/0000-0099/0070.Climbing%20Stairs/README.md)

## Description

<p>You are climbing a stair case. It takes <em>n</em> steps to reach to the top.</p>

<p>Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?</p>

<p><strong>Note:</strong> Given <em>n</em> will be a positive integer.</p>

<p><strong>Example 1:</strong></p>

<pre>

<strong>Input:</strong> 2

<strong>Output:</strong> 2

<strong>Explanation:</strong> There are two ways to climb to the top.

1. 1 step + 1 step

2. 2 steps

</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> 3

<strong>Output:</strong> 3

<strong>Explanation:</strong> There are three ways to climb to the top.

1. 1 step + 1 step + 1 step

2. 1 step + 2 steps

3. 2 steps + 1 step

</pre>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        a, b = 0, 1
        for _ in range(n):
            a, b = b, a + b
        return b
```

### **Java**

```java
class Solution {
    public int climbStairs(int n) {
        int a = 0, b = 1;
        for (int i = 0; i < n; ++i) {
            int c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int climbStairs(int n) {
        int a = 0, b = 1;
        for (int i = 0; i < n; ++i) {
            int c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
};
```

### **JavaScript**

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function (n) {
  let a = 0,
    b = 1;
  for (let i = 0; i < n; ++i) {
    const c = a + b;
    a = b;
    b = c;
  }
  return b;
};
```

### **Go**

```go
func climbStairs(n int) int {
    a, b := 0, 1
    for i := 0; i < n; i++ {
        a, b = b, a + b
    }
    return b
}
```

### **...**

```

```

<!-- tabs:end -->
