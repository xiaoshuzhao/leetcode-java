# 栈与队列

栈是一种**后进先出**（Last in First Out）的数据结构，简称 **LIFO**

队列是一种**先进先出**（First in First Out）的数据结构，简称 **FIFO**



[232 - 用栈实现队列](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/225.%20%E7%94%A8%E9%98%9F%E5%88%97%E5%AE%9E%E7%8E%B0%E6%A0%88.md)

[225 - 用队列实现栈](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/225.%20%E7%94%A8%E9%98%9F%E5%88%97%E5%AE%9E%E7%8E%B0%E6%A0%88.md)

[155 - 最小值栈](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/155.%E6%9C%80%E5%B0%8F%E5%80%BC%E6%A0%88.md)

[394 - 解码字符串](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/394.%20%E8%A7%A3%E7%A0%81%E5%AD%97%E7%AC%A6%E4%B8%B2.md)

[150 - 逆波兰表达式求值](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/150.%E9%80%86%E6%B3%A2%E5%85%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%B1%82%E5%80%BC%20.md)

[1047 - 删除字符串中的所有相邻重复项](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/1047.%20%E5%88%A0%E9%99%A4%E5%AD%97%E7%AC%A6%E4%B8%B2%E4%B8%AD%E7%9A%84%E6%89%80%E6%9C%89%E7%9B%B8%E9%82%BB%E9%87%8D%E5%A4%8D%E9%A1%B9.md)

[2390 - 移除字符串里的*](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/2390.%20%E7%A7%BB%E9%99%A4%E5%AD%97%E7%AC%A6%E4%B8%B2%E9%87%8C%E7%9A%84*.md)



## 括号匹配

[20 - 有效的括号E](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/20.%20%E6%9C%89%E6%95%88%E7%9A%84%E6%8B%AC%E5%8F%B7.md)

[32 - 最长有效括号H](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/32.%20%E6%9C%80%E9%95%BF%E6%9C%89%E6%95%88%E6%8B%AC%E5%8F%B7.md)

[921 - 使括号有效的最少添加M](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/921.%20%E4%BD%BF%E6%8B%AC%E5%8F%B7%E6%9C%89%E6%95%88%E7%9A%84%E6%9C%80%E5%B0%91%E6%B7%BB%E5%8A%A0.md)

[1541 - 平衡括号字符串的最少插入次数M](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/1541.%E5%B9%B3%E8%A1%A1%E6%8B%AC%E5%8F%B7%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%9C%80%E5%B0%91%E6%8F%92%E5%85%A5%E6%AC%A1%E6%95%B0.md)


用栈后进先出的特点进行括号匹配；
1. 是否匹配：如果括号类型多，则使用Hash Map和栈中的值进行匹配
2. 插入数量：如果只有一类括号，则可维护插入数量和对右括号的需求量两个常量
3. 最长距离：可将对应下标存入栈中，而不是值；计算符合条件的下标直接的距离；这里需要记录起点的位置, 先-1入栈，或者start记录



## 单调栈

[496 - 下一个更大的元素I](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/496.%20%E4%B8%8B%E4%B8%80%E4%B8%AA%E6%9B%B4%E5%A4%A7%E7%9A%84%E5%85%83%E7%B4%A0I.md)

[503 - 下一个更大元素 II](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/503.%20%E4%B8%8B%E4%B8%80%E4%B8%AA%E6%9B%B4%E5%A4%A7%E5%85%83%E7%B4%A0%20II.md)

[739 - 每日温度](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/739.%20%E6%AF%8F%E6%97%A5%E6%B8%A9%E5%BA%A6.md)

[42 - 接雨水](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/42.%20%E6%8E%A5%E9%9B%A8%E6%B0%B4%E2%98%94%EF%B8%8F.md)

[907 - 子数组最小值的和](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/907.%20%E5%AD%90%E6%95%B0%E7%BB%84%E6%9C%80%E5%B0%8F%E5%80%BC%E7%9A%84%E5%92%8C.md)

用单调栈依次从后往前筛选出更大的元素，for循环遍历数组元素，while循环筛选栈中比当前值较小的值（数组中当前值后面 的比当前值小的值），每次栈顶元素就是比当前值大的值

503 - 环形数组，遍历2遍，用i = n*2-1, index 为i % n

739 - 每日温度，需要计算下一个温暖日的距离有几天，计算距离，入栈下标index

42 - 单调递减栈，遇到高柱子需要计算前面已接的雨水，计算左右距离和上下高度，存index

```java
int[] nextGreaterElement(int[] nums) {
    int n = nums.length;
    int[] res = new int[n];
    Deque<Integer> stack = new LinkedList<Integer>();
    for (int i = n - 1; i >= 0; i--) { // 倒序入栈
        while (!stack.isEmpty() && stack.peek() <= nums[i]) {
						stack.pop(); 
        }
      	// 若是栈为空，则后面没有较大值；若是不为空，则栈顶元素就是更大值
        res[i] = stack.isEmpty() ? -1 : stack.peek();
        stack.push(nums[i]);
    }
return res; }
```





## 滑动窗口-单调队列

[239 - 滑动窗口最大值](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/239.%20%E6%BB%91%E5%8A%A8%E7%AA%97%E5%8F%A3%E7%9A%84%E6%9C%80%E5%A4%A7%E5%80%BC.md)











## 补充知识



1. 顺序存储的栈叫做**顺序栈**

顺序栈使用数组实现，下标为 0 的一端作为栈底，使用 top 做为栈顶，它来指示当前栈顶元素的位置，默认 top = -1 时为空栈。

<img src="/Users/sugar/Documents/leetcode/pic/640.png" alt="640" style="zoom:50%;" />

2. 链式存储的栈叫做**链栈**。

链栈用单链表实现，一般尾节点为栈底，使用头指针指向的节点作为栈顶，不需要头节点。top = NULL 为空栈。

![640 (1)](/Users/sugar/Documents/leetcode/pic/640 (1).png)
