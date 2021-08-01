## 题目描述：
This time, you are supposed to find A+B where A and B are two polynomials.

## 输入格式:
Each input file contains one test case. Each case occupies 2 lines, and each line contains the information of a polynomial:
K N<sub>1</sub> a<sub>N1</sub> N<sub>2</sub> a<sub>N2</sub> ...  N<sub>K</sub> a<sub>NK</sub> where K is the number of nonzero terms in the polynomial, N<sub>i</sub> and a<sub>Ni</sub> (i=1,2,⋯,K) are the exponents and coefficients, respectively. It is given that 1≤K≤10，0≤N<sub>K</sub> \< ... \< N<sub>2</sub> \< N<sub>1</sub> ≤1000.

## 输出格式:
For each test case you should output the sum of A and B in one line, with the same format as the input. Notice that there must be NO extra space at the end of each line. Please be accurate to 1 decimal place.  

## 输入样例:
```
2 1 2.4 0 3.2
2 2 1.5 1 0.5
```

## 输出样例:
```
3 2 1.5 1 2.9 0 3.2
```

## 题目来源:
PAT : https://pintia.cn/problem-sets/994805342720868352/problems/994805526272000000

## 算法标签:
模拟

## 记录时间:
azwcl : 2021-08-01 23:00

## 思路:
系数相同的指数计算加起来即可，不难，主要看懂题目即可。  
最后倒序排列输出即可！

## AC代码:
```cpp
#include <iostream>
using namespace std;
const int N = 1010;
double sum[N]; // 指数的和

int main()
{
    int aknum, bknum;
    cin >> aknum;
    int tmp = 0;// 临时变量
    double tmpval; // 临时变量记录的指数位
    for(int i = 0; i < aknum; i++) {
        cin >> tmp;
        cin >> tmpval;
        sum[tmp] += tmpval;
    }
    cin >> bknum;
    for(int i = 0; i < bknum; i++) {
        cin >> tmp;
        cin >> tmpval;
        sum[tmp] += tmpval;
    }

    int cnt = 0;
    for(int i = 0; i < N; i++) 
        if(sum[i] != 0)
            cnt++; // 计算指数不为 0 的个数
    
    printf("%d", cnt);
    for(int i = N - 1; i >= 0; i--)
    {
        if(sum[i] != 0)
            printf(" %d %0.1f", i, sum[i]); // 按倒序输出指数不为 0 的结果
    }

    return 0;
}
```