# 关于CF1539B Love Song题目的理解

[传送门](https://www.luogu.com.cn/problem/CF1539B)

本题若暴力硬解必然会出现**TLE**，所以说考虑另选方法，由于是新手也想不出什么可靠的方法，于是打开题解，发现了前缀和的方法，以下是学习前缀和的过程。

## 前缀和

前缀和是一种重要的预处理，能大大降低查询的时间复杂度。可以简单理解为“数列的前$n$项的和”。

>例题0：
>
>有 $N$个的正整数放到数组$A$里，现在要求一个新的数组 B，新数组的第 $i$个数 $B[i]$是原数组 第 0 到第 $i$ 个数的和。
>
>输入：
>
>```cmake
>5
>1 2 3 4 5
>```
>
>输出：
>
>```
>1 3 6 10 15
>```
>
>
>解题思路：
>
>对于这道题，我们有两个做法：
>
>- 将$A$数组逐个累加依次放入$B$数组中
>- 递推$$B[i] = B[i-1] + A[i]$$,前提是$B[0]=A[0]$
>
>
>参考代码：
>
>```cpp
>#include<iostream>
>#define NUM 500
>using namespace std;
>int main(){
>   int n;
>   cin>>n;
>   int a[NUM];
>   for(int i=0;i<n;i++){
>       cin>>a[i];
>   }
>   int b[NUM];
>   b[0]=a[0];
>   for(int i=1;i<n;i++){
>       b[i]=b[i-1]+a[i];
>   }
>   for(int i=0;i<n;i++){
>       cout<<b[i]<<' ';
>   }
>}
>```

>例题1：
>
>求一个数组的连续子数组的总个数，其中连续是指元素在数组中的索引连续。比如[1,3,4],其连续的子数组有：[1], [3], [4], [1,3], [3,4] , [1,3,4]，你需要返回 6。
>
>输入：
>
>```
>3
>1 3 4
>```
>
>输出：
>
>```
>6
>```
>
>解题思路：
>
>同例题0一样，找递推即可——
>
>以引索为0结尾的子数组的个数+
>
>以引索为1结尾的子数组的个数+
>
>以引索为2结尾的子数组的个数+
>
>...
>
>这无疑是完备的；
>
>参考代码：
>
>```cpp
>
>```



https://segmentfault.com/a/1190000025178927

`在继续学习的工程中发现了需要学习滑动窗口，下面是学习滑动窗口的过程`

## 滑动窗口

[参考文章](https://github.com/azl397985856/leetcode/blob/master/thinkings/slide-window.md)

### 常见套路

滑动窗口主要用来处理连续问题。比如题目求解“连续子串 xxxx”，“连续子数组 xxxx”，就应该可以想到滑动窗口。

从类型上有：

- 固定窗口的大小
- 窗口大小不固定，求解满足条件的最大的窗口
- 窗口大小不固定，求解满足条件的最小的窗口

下面来逐个分析

#### 固定窗口的大小

对于固定的窗口，我们只需要给出左右指针l和r，分别代表窗口的左右两端，并且保证：

1. $l$ 初始化为0
2. 初始化r，使得r - l + 1 等于窗口的大小
3. 同时移动 l 和 r
4. 判断窗口内的元素是否满足条件，
   - 满足，判断是否需要更新最优解，
   - 不满足，移动左右指针

#### 可变窗口的大小

同样给出左右两个指针l和r，但后面的操作略微有些不同

1. l和r都初始化为0
2. r指针向右移动一步
3. 判断窗口是否满足条件
   - 满足，判断是否需要更新最优解
     - 如果需要更新最优解 ，尝试通过移动l指针来缩小窗口的大小
   - 不满足，继续移动r指针

形象一点来看的话，就是r指针一直向右边移动，直到满足条件，才开始起到窗口收缩的效果。

>
>例题0：
>
>给定一个字符串，求其中不含有重复字符的最长字串的长度
>
>输入：
>
>```
>abcabcbb
>```
>
>输出
>
>```
>3
>```
>
>解题思路：
>
>利用可变窗口
>
>参考代码
>
>```cpp
>
>```
>
>






