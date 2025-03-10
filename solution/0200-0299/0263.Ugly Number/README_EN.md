# [263. Ugly Number](https://leetcode.com/problems/ugly-number)

[中文文档](/solution/0200-0299/0263.Ugly%20Number/README.md)

## Description

<p>Write a program to check whether a given number is an ugly number.</p>

<p>Ugly numbers are <strong>positive numbers</strong> whose prime factors only include <code>2, 3, 5</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>

<strong>Input:</strong> 6

<strong>Output:</strong> true

<strong>Explanation: </strong>6 = 2 &times;&nbsp;3</pre>

<p><strong>Example 2:</strong></p>

<pre>

<strong>Input:</strong> 8

<strong>Output:</strong> true

<strong>Explanation: </strong>8 = 2 &times; 2 &times;&nbsp;2

</pre>

<p><strong>Example 3:</strong></p>

<pre>

<strong>Input:</strong> 14

<strong>Output:</strong> false 

<strong>Explanation: </strong><code>14</code> is not ugly since it includes another prime factor <code>7</code>.

</pre>

<p><strong>Note:</strong></p>

<ol>
    <li><code>1</code> is typically treated as an ugly number.</li>
    <li>Input is within the 32-bit signed integer range:&nbsp;[&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1].</li>
</ol>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def isUgly(self, n: int) -> bool:
        if n < 1:
            return False
        while n % 2 == 0:
            n //= 2
        while n % 3 == 0:
            n //= 3
        while n % 5 == 0:
            n //= 5
        return n == 1
```

### **Java**

```java
class Solution {
    public boolean isUgly(int n) {
        if (n < 1) return false;
        while (n % 2 == 0) {
            n /= 2;
        }
        while (n % 3 == 0) {
            n /= 3;
        }
        while (n % 5 == 0) {
            n /= 5;
        }
        return n == 1;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    bool isUgly(int n) {
        if (n < 1) return false;
        while (n % 2 == 0) {
            n /= 2;
        }
        while (n % 3 == 0) {
            n /= 3;
        }
        while (n % 5 == 0) {
            n /= 5;
        }
        return n == 1;
    }
};
```

### **JavaScript**

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isUgly = function (n) {
  if (n < 1) return false;
  while (n % 2 == 0) {
    n /= 2;
  }
  while (n % 3 == 0) {
    n /= 3;
  }
  while (n % 5 == 0) {
    n /= 5;
  }
  return n == 1;
};
```

### **...**

```

```

<!-- tabs:end -->
