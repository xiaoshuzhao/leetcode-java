# Array



[11 - 收集最多水的容器 =]

[33. 搜索旋转排序数组=]

[152. 乘积最大子数组=]

[238. 除自身以外数组的乘积=]

[252 - 会议室=]

[253. 会议室II=]



## 二分法

[704. 二分查找]

[875. 爱吃香蕉的KOKO]

[35. 搜索插入位置]

[240. 有序矩阵查找 M]

[287. 找到重复值 M]

[69. 求解平方根]

[540. 有序数组中的单个元素]

[153. 旋转数组的最小数字]

[34. 查找开始结束区间]

[128. 第一个错误的版本]



## 双指针

[977. 有序数组的平方]

[189. 旋转数组]

[283. 移动零 E]

[88. 归并两个有序数组]



## 滑动窗口

[209. 长度最小的子数组]

[76. 最小覆盖子串]



## 模拟

[54. 螺旋矩阵 I]

[59. 螺旋矩阵 II]



## 前缀和

[724. 寻找中心下标]

[1365. 比当前数小的数]

[56. 合并区间]





[566. 重塑矩阵 E]

[485. 最长的连续1 E]

[378. 有序矩阵的 Kth Element]

[645. 错误的集合]

[667.优美的排列 II]

[697. 数组的度]

[766. 对角元素相等的矩阵]

[565. 数组嵌套]

[769. 最多能完成排序的块]

[744. 大于给定元素的最小元素]





















## 【二分法】

优点：将整个搜索循环排除掉了一半

必要元素：最小值，最大值，范围；比较对象



**【左闭右闭】**

```java
[left, right]
// left == right 有意义，即target有可能 == left == right
int left = 0, right = nums.length - 1;
while(left <= right){
    if (nums[mid] == target){
        return mid;
     // 即每次将区间排除掉已知数，nums[mid]， mid - 1或mid + 1
    } else if (nums[mid] > target){
        right = mid - 1;
    } else if(nums[mid] < target){
        left = mid + 1;
    }
}
```



**【左闭右开】**

```java
[left, right)
// left == right 没有意义，即target不可能 == left == right
int left = 0, right = nums.length;
while(left < right){
    if (nums[mid] == target){
        return mid;
     // 即每次将right赋值给mid, 因为nums[mid]不可能等于target
    } else if (nums[mid] > target){
        right = mid;
    } else if(nums[mid] < target){
        left = mid + 1; //left 是闭区间，left有可能== target
    }
}
```



**注意事项：**

```text
1. left 和 right 是index

2. mid = (left + right) / 2 容易溢出！因为left+right很容易超过 int 范围！而mid = left + (right - left) / 2 不容易溢出；

3. >>右移位运算符为二进制右移， 计算机计算二进制会更快

4. right 的赋值决定了比较方式，因为要确保最两边的值能被取到：
如果right = n - 1(数组最后一位)，则需要while(left <= right), 因为比如如果target==nums[right]，则如要取到最后1位，需要left == right
如果right = n(数组多出1位)，则需要while(left < right)，刚好取到最后一位
```



