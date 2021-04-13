## 题目描述：
Redraiment是走梅花桩的高手。Redraiment总是起点不限，从前到后，往高的桩子走，但走的步数最多，不知道为什么？你能替Redraiment研究他最多走的步数吗？  

## 输入格式:
输入多行，先输入数组的个数，再输入相应个数的整数  

## 输出格式:
输出结果  

## 数据范围:

## 输入样例:
```
6
2 5 1 5 4 5 
3
3 2 1
```

## 输出样例:
```
3
1
```

## 题目来源:
牛客网 : https://www.nowcoder.com/questionTerminal/24e6243b9f0446b081b1d6d32f2aa3aa

## 算法标签:
动态规划

## 记录时间:
azwcl : 2021-04-13 10:17

## 思路:
**思想：本题就是一个求解最大的递增子序列即可！**  

例如：我们现在给定一个长度为5的数组list：[4, 5, 1, 3, 6],那么最大的递增数组则是：[1, 3, 6]或者[4, 5, 6],长度是3.  

则我们该题目我们可以利用动态规划的思想来写，设置一个dp[i]是记录上面数组list[i]为末尾元素的最长递增子序列。  

算法的过程：  
i = 0；则dp[i] = 1，因为此时A[i] = 4,此时只有一个元素构成了子序列  
i = 1；则dp[i] = 2，因为此时A[i] = 5,dp[i] = d[0] + 1;  
i = 2；则dp[i] = 1，因为此时A[i] = 1,前面并没有一个元素大于A[i]，则dp[i] = 1；  
i = 3；则dp[i] = 2，因为此时A[i] = 3，那么前面只有A[2]小于A[i]，也就是dp[i] = dp[2] + 1 = 2;  
i = 4；则dp[i] = 3，因为此时A[I] = 4，那么前面有A[0],A[1],A[2],A[3]小于A[i],此时，这些元素的dp[i]最大的是2，那么就是dp[i] = max(前面最大的dp数组元素) +1；  

也就是说，求最大的递增子序列，我们可以，先从数组元素第一位开始遍历，从第一位开始求解以当前元素作为末尾元素的时候数组的最大的递增子序列的元素个数，后面元素i的最大递增子序列元素个数就是前面比list[i]小的元素的最大递增子序列元素个数 + 1。  

## AC代码:
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    int n;
    while(cin >> n)
    {
        vector<int> list(n), dp(n);
        for(int i = 0; i < n; i++) scanf("%d", &list[i]);

        for(int i = 0; i < n; i++)
        {
            int tmp = 0;
            for(int j = 0; j < n; j++)
                if(list[i] > list[j] && tmp < dp[j]) tmp = dp[j];
            dp[i] = tmp + 1;
        }

        int res = dp[0];

        for(int i = 0; i < n; ++i)
            res = max(res, dp[i]);
        
        cout << res << endl;
    }

    return 0;
}
```