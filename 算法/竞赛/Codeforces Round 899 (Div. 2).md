# Codeforces Round 899 (Div. 2)

## 概述

- 通过：AB
- 补题：CDE

## 题解

### [E Two Permutations(easy)](https://codeforces.com/contest/1882/problem/E1)

- 题目中的操作与以下等价：将原序列前面加一个$0,p_1,p_2,\dots,p_n$，每一次操作就是把0与另一个元素交换，最终得到$0,1,2,\dots,n$的一个循环排列
  - 即$0,2,4,1,3\to1,2,4,0,3\to1,2,0,4,3\to1,2,3,4,0$
  - 与**每一种循环排列**比较就能得到不同的方案，最终结果就是两个序列操作奇偶性相同的解的较大值（相同奇偶性可以相互转化的）
- 对于每种情况，可以如下计算：
  - 构图，连接$i与p[a[i]]$，最少操作次数就是n+1-环数+2*不含0的非孤立点环数（p表示目标数组中值a[i]的下标）
  - 如$0,4,2,1,3\to4,0,1,2,3$
    - <img src="https://thdlrt.oss-cn-beijing.aliyuncs.com/image-20230926105942834.png" alt="image-20230926105942834" style="zoom:33%;" />
    - 即$5-3+1*2=4$
  - 对于一个大小为n环，需要操作n-1次使其与目标一致，而对于不含0的，多了把0换入换出这个过程，因此要加2
  - 注意每步操作数实际是与0交换的元素与0的距离（向右距离）
- 复杂度$O(n^2+m^2)$

