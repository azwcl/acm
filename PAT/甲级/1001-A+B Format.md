## 题目描述：
Calculate a+b and output the sum in standard format -- that is, the digits must be separated into groups of three by commas (unless there are less than four digits).

## 输入格式:
Each input file contains one test case. Each case contains a pair of integers a and b where −10<sup>6</sup>≤a,b≤10<sup>6</sup>. The numbers are separated by a space.

## 输出格式:
For each test case, you should output the sum of a and b in one line. The sum must be written in the standard format.

## 数据范围:

## 输入样例:
```
-1000000 9
```

## 输出样例:
```
-999,991
```

## 题目来源:
PAT : https://pintia.cn/problem-sets/994805342720868352/problems/994805528788582400

## 算法标签:
模拟  

## 记录时间:
azwcl : 2021-07-31 22:50

## 思路:
模拟题，主要是看懂题意，格式化计算机结果即可，每三位给一个","号即可。  

## AC代码:
```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    int a, b;
    while(cin >> a)
    {
        cin >> b;
        int c = a + b;
        if(c < 0) {
            printf("-");
            c = -c;
        }

        string str = to_string(c);
        string res = ""; // 记录规格化之后的字符串
        int flag = 0;

        for(int i = str.length() - 1; i >= 0; i--) 
        {
            res += str[i];
            flag ++;
            if(flag == 3 && i != 0) { // 这里 i 不能等于 0， 否则的话，会出现 200 -> ,200 的情况
                res += ","; 
                flag = 0;
            }
        }

        // 逆序即可
        for(int j = res.length() - 1; j >= 0; j--)
            printf("%c", res[j]);
    }
    return 0;
}
```