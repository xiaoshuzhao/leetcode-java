# 栈与队列



## 括号匹配

[20 - 有效的括号E](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/20.%20%E6%9C%89%E6%95%88%E7%9A%84%E6%8B%AC%E5%8F%B7.md)

[32 - 最长有效括号H](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/32.%20%E6%9C%80%E9%95%BF%E6%9C%89%E6%95%88%E6%8B%AC%E5%8F%B7.md)

[921 - 使括号有效的最少添加M](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/921.%20%E4%BD%BF%E6%8B%AC%E5%8F%B7%E6%9C%89%E6%95%88%E7%9A%84%E6%9C%80%E5%B0%91%E6%B7%BB%E5%8A%A0.md)

[1541 - 平衡括号字符串的最少插入次数M](https://github.com/xiaoshuzhao/leetcode-notes-java/blob/main/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84/%E6%A0%88%E4%B8%8E%E9%98%9F%E5%88%97/1541.%E5%B9%B3%E8%A1%A1%E6%8B%AC%E5%8F%B7%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%9C%80%E5%B0%91%E6%8F%92%E5%85%A5%E6%AC%A1%E6%95%B0.md)



用栈后进先出的特点进行括号匹配；

1. 是否匹配：如果括号类型多，则使用Hash Map和栈中的值进行匹配

2. 插入数量：如果只有一类括号，则可维护插入值和对右括号的需求值两个常量

3. 最长距离：可将对应下标存入栈中，而不是值；计算符合条件的下标直接的距离；这里需要记录起点的位置
