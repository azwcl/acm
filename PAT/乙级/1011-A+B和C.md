## 题目描述：
给定区间 [−2<sup>​31</sup>​​ ,2<sup>​31</sup>​​ ] 内的 3 个整数 A、B 和 C，请判断 A+B 是否大于 C。  

## 输入格式:
输入第 1 行给出正整数 T (≤10)，是测试用例的个数。随后给出 T 组测试用例，每组占一行，顺序给出 A、B 和 C。整数间以空格分隔。  

## 输出格式:
对每组测试用例，在一行中输出 Case #X: true 如果 A+B>C，否则输出 Case #X: false，其中 X 是测试用例的编号（从 1 开始）。  

## 输入样例:
```
4
1 2 3
2 3 4
2147483647 0 2147483646
0 -2147483648 -2147483647
```

## 输出样例:
```
Case #1: false
Case #2: true
Case #3: true
Case #4: false
```

## 题目来源:
PAT: https://pintia.cn/problem-sets/994805260223102976/problems/994805312417021952  

## 算法标签:
简单练习

## 记录时间:
azwcl : 2021-03-21 12:06

## 思路:
运算即可

## AC代码:
```cpp
#include <cstdio>
#include <cstring>
#include <iostream>
#include <string>
//使用long，注意！
using namespace std;

int main()
{
	int n;
	cin >> n;
	for(int i = 0; i < n; i++){
		long num1, num2, num3;
		scanf("%ld %ld %ld",&num1,&num2,&num3);
		if(num1 + num2 > num3){
			printf("Case #%d: true\n",i+1);
		}else{
			printf("Case #%d: false\n",i+1);
		}
	}
	return 0;
}
```