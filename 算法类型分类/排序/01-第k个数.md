## 题目描述：
给定一个长度为 n 的整数数列，以及一个整数  k ，请用快速选择算法求出数列从小到大排序后的第 k 个数。

## 输入格式:
第一行包含两个整数 n 和 k。  
第二行包含 n 个整数（所有整数均在 1∼109 范围内），表示整数数列。  

## 输出格式:
输出一个整数，表示数列的第 k 小数。  

## 数据范围:
1≤n≤100000  
1≤k≤n

## 输入样例:
```
5 3
2 4 1 5 3
```

## 输出样例:
```
3
```

## 题目来源:
ACWING: https://www.acwing.com/problem/content/788/
## 算法标签:
排序

## 记录时间:
2021-03-20 16:36

## 思路:
直接排序结束

## AC代码:
```cpp
#include <iostream>
#include <algorithm>
using namespace std;
const int N = 100010;
int n, k, nums[N];

int main()
{
    scanf("%d %d", &n, &k);
    for(int i = 0; i < n; i++) scanf("%d", &nums[i]);
    sort(&nums[0], &nums[n]);
    cout << nums[k-1];
    return 0;
}
```