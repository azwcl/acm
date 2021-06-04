## 题目描述：
实现 pow(x, n) ，即计算 x 的 n 次幂函数（即，x<sup>n</sup>）。  

## 数据范围:
-100.0 < x < 100.0  
-2<sup>31</sup> <= n <= 2<sup>31</sup>-1  
-10<sup>4</sup> <= x<sup>n</sup> <= 10<sup>4</sup>  

## 示例1:
```
输入：x = 2.00000, n = 10
输出：1024.00000
```

## 示例2:
```
输入：x = 2.10000, n = 3
输出：9.26100
```

## 示例3:
```
输入：x = 2.00000, n = -2
输出：0.25000
解释：2-2 = 1/22 = 1/4 = 0.25
```

## 题目来源:
LeetCode : https://leetcode-cn.com/problems/powx-n/  

## 算法标签:
快速幂

## 记录时间:
azwcl : 2021-06-04 17:28  

## 思路:
利用快速幂计算。  

## AC代码:
```cpp
class Solution {
public:
    double qpow(double x, long long n) {
        if(n == 0) return 1;
        else if(n % 2 == 0) {
            double tmp = qpow(x, n/2);
            return tmp * tmp;
        }
        else {
            return qpow(x, n - 1) * x;
        }
    }

    double myPow(double x, int n) {
        long long num = n;

        if(n < 0) {
            return 1 / qpow(x, 0-num);// 防止 0-num的时候整数溢出
        }
        else return qpow(x, num);
    }
};
```