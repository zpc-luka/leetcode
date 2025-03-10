# [11. 盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water)

[English Version](/solution/0000-0099/0011.Container%20With%20Most%20Water/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->
<p>给你 <em>n</em> 个非负整数 <em>a</em><sub>1</sub>，<em>a</em><sub>2，</sub>...，<em>a</em><sub>n，</sub>每个数代表坐标中的一个点&nbsp;(<em>i</em>,&nbsp;<em>a<sub>i</sub></em>) 。在坐标内画 <em>n</em> 条垂直线，垂直线 <em>i</em>&nbsp;的两个端点分别为&nbsp;(<em>i</em>,&nbsp;<em>a<sub>i</sub></em>) 和 (<em>i</em>, 0)。找出其中的两条线，使得它们与&nbsp;<em>x</em>&nbsp;轴共同构成的容器可以容纳最多的水。</p>

<p><strong>说明：</strong>你不能倾斜容器，且&nbsp;<em>n</em>&nbsp;的值至少为 2。</p>

<p>&nbsp;</p>

![](./images/question_11.jpg)

<p><small>图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为&nbsp;49。</small></p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[1,8,6,2,5,4,8,3,7]
<strong>输出：</strong>49</pre>

## 解法

<!-- 这里可写通用的实现逻辑 -->

双指针解决。

一开始，我们考虑相距最远的两个柱子所能容纳水的面积。水的宽度是两根柱子之间的距离，而水的高度取决于两根柱子之间较短的那个。

- 当前柱子是最两侧的柱子，水的宽度最大，其他的组合，水的宽度都比这个小；
- 当前左侧柱子较短，决定了水的高度。如果移动左侧的柱子，新的水面高度不确定，但一定不会超过右侧的柱子高度；
- 如果移动右侧的柱子，新的水面高度一定不会超过左侧的柱子高度，也就是不会超过当前的水面高度。

可见，如果固定左侧的柱子，向内移动右侧的柱子，水的高度一定不会增加，且宽度一定减少，所以水的面积一定减少。所以左侧的柱子跟右侧其他柱子的组合，都可以排除了。也就是代码中的 `i++`。

移动左侧的柱子中，重复进行上面的操作。

在此过程中，我们不断排除掉无法成为构成最大值的柱子组合，而每一次都获取到可能为最大值的面积 t。那么遍历结束之后，我们就可以得到最大值。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        i, j = 0, len(height) - 1
        res = 0
        while i < j:
            t = (j - i) * min(height[i], height[j])
            res = max(res, t)
            if height[i] < height[j]:
                i += 1
            else:
                j -= 1
        return res
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0, j = height.length - 1;
        int res = 0;
        while (i < j) {
            int t = (j - i) * Math.min(height[i], height[j]);
            res = Math.max(res, t);
            if (height[i] < height[j]) ++i;
            else --j;
        }
        return res;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int i = 0, j = height.size() - 1;
        int res = 0;
        while (i < j) {
            int t = (j - i) * min(height[i], height[j]);
            res = max(res, t);
            if (height[i] < height[j]) ++i;
            else --j;
        }
        return res;
    }
};
```

### **Go**

```go
func maxArea(height []int) int {
    i, j := 0, len(height) - 1
    res := 0
    for i != j {
        t := (j - i) * min(height[i], height[j])
        res = max(res, t)
        if height[i] < height[j] {
            i++
        } else {
            j--
        }
    }
    return res
}

func min(a, b int) int {
    if a > b {
        return b
    }
    return a
}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}
```

### **JavaScript**

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function (height) {
  let i = 0,
    j = height.length - 1;
  let res = 0;
  while (i < j) {
    const t = (j - i) * Math.min(height[i], height[j]);
    res = Math.max(res, t);
    if (height[i] < height[j]) ++i;
    else --j;
  }
  return res;
};
```

### **...**

```

```

<!-- tabs:end -->
