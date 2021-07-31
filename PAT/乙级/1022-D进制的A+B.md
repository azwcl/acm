## 题目描述：
输入两个非负 10 进制整数 A 和 B (≤2<sup>​30</sup>−1)，输出 A+B 的 D (1<D≤10)进制数。  

## 输入格式:
输入在一行中一次给出 3 个整数 A、B 和 D。  

## 输出格式:
输出 A+B 的 D 进制数。  

## 数据范围:
A 和 B (≤2<sup>​30</sup>−1)

## 输入样例:
```
123 456 8
```

## 输出样例:
```
1103
```

## 题目来源:
PAT: https://pintia.cn/problem-sets/994805260223102976/problems/994805299301433344  

## 算法标签:
数学、进制转换、模拟  

## 记录时间:
azwcl : 2021-03-29 16:13  

## 思路:
因为数据范围小，直接简单模拟进制转换的过程即可

## AC代码:
```cpp
#include <iostream>
#include <vector>
using namespace std;

long long a, b;

int main()
{
    int jin;
    cin >> a >> b >> jin;
    long res = a + b;
    
    vector<int> vc;
    // 用do...while循环：防止一开始输入0，导致没有输出。
    do{
        int tmp = res % jin;
        res /= jin;
        vc.push_back(tmp);
    }while(res != 0);
    
    
    for(int i = vc.size() - 1; i >= 0; i--) cout << vc[i];
    
    return 0;
}
```