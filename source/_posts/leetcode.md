layout: '[layout]'
title: Leetcode学习笔记（python）
date: 2016-06-10 16:34:19
tags: 
- python
- 学习笔记
- leetcode

categories: 笔记
---

我爱学习，学习使我快乐！


<!--more-->

### 326. Power of Three
Given an integer, write a function to determine if it is a power of three.（判断一个数是否是3的次方数，不使用循环和迭代）

>由于输入是int，正数范围是0-2^31，在此范围中允许的最大的3的次方数为3^19=1162261467，那么我们只要看这个数能否被n整除即可。

```
class Solution(object):
    def isPowerOfThree(self, n):
        """
        :type n: int
        :rtype: bool
        """
        return n > 0 and 1162261467 % n ==0
```
***
### 152. Maximum Product Subarray
Find the contiguous subarray within an array (containing at least one number) which has the largest product.For example, given the array [2,3,-2,4],the contiguous subarray [2,3] has the largest product = 6
从数组（至少包含一个数字）中找出一个连续的子数组，该子数组的乘积最大。

>对于Product Subarray，要考虑到一种特殊情况，即负数和负数相乘：如果前面得到一个较小的负数，和后面一个较大的负数相乘，得到的反而是一个较大的数，如{2，-3，-7}，所以，我们在处理乘法的时候，除了需要维护一个局部最大值，同时还要维护一个局部最小值，由此，可以写出如下的转移方程式：`big, small=max(n, n*big, n*small), min(n, n*big, n*small)`

```
class Solution(object):
    def maxProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        maximum=big=small=nums[0]
        for n in nums[1:]:
            big, small=max(n, n*big, n*small), min(n, n*big, n*small)
            maximum=max(maximum, big)
        return maximum
```


### 155. Min Stack
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.

>利用元组tuple，同时储存数和最小值。

```
class MinStack(object):

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.q = []


    def push(self, x):
        """
        :type x: int
        :rtype: void
        """
        curMin = self.getMin()
        if curMin == None or x < curMin:
            curMin = x
        self.q.append((x, curMin));

    def pop(self):
        """
        :rtype: void
        """
        self.q.pop()

    def top(self):
        """
        :rtype: int
        """
        if len(self.q) == 0:
            return None
        else:
            return self.q[-1][0]

    def getMin(self):
        """
        :rtype: int
        """
        if len(self.q) == 0:
            return None
        else:
            return self.q[-1][1]
```

***
### 198. House Robber
题目描述：你是一名专业强盗，计划沿着一条街打家劫舍。每间房屋都储存有一定数量的金钱，唯一能阻止你打劫的约束条件就是：由于房屋之间有安全系统相连，如果同一个晚上有两间相邻的房屋被闯入，它们就会自动联络警察，因此不可以打劫相邻的房屋。给定一列非负整数，代表每间房屋的金钱数，计算出在不惊动警察的前提下一晚上最多可以打劫到的金钱数。
>解题思路：
这道题的本质相当于在一列数组中取出一个或多个不相邻数，使其和最大。 这是一道动态规划问题。 我们维护一个一位数组dp，其中dp[i]表示到i位置时不相邻数能形成的最大和。 对于第i个房间我们的选择是偷和不偷， 如果决定是偷 则第i-1个房间必须不偷 那么 这一步的就是` dp[i] = nums(i-1) + dpNotTake[i -1]` , 假设dp[i]表示打劫到第i间房屋时累计取得的金钱最大值.如果是不偷， 那么上一步就无所谓是不是已经偷过， dp[i] = dp[i -1 ]， 因此 `dp[i] =max(dpNotTake[i-1 ] + nums(i-1), dp[i-1] )` 其中`dpNotTake[i-1]=dp[i-2]`利用动态规划，状态转移方程：`dp[i] = max(dp[i - 1], dp[i - 2] + num[i - 1])`其中，dp[i]表示打劫到第i间房屋时累计取得的金钱最大值。

状态转移方程：
dp[0] = num[0] （当i=0时）
dp[1] = max(num[0], num[1]) （当i=1时）
dp[i] = max(num[i] + dp[i - 2], dp[i - 1])   （当i !=0 and i != 1时）

```
class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        last, now = 0, 0
        for i in nums: last, now = now, max(last + i, now)
        return now
```
