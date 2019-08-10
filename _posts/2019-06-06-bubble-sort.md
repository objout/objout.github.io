---
layout: post
title: 冒泡排序
tags: algorithm
categories: C语言
---

<hr />
1. 比较序列中相邻的两个元素，如果位置错误，就交换它们的值,对所有元素重复这一步骤，直到元素越来越少。
2. 最差时间复杂度:O(n<sup>2</sup>)
3. 最优时间复杂度:O(n)
4. 平均时间复杂度:O(n<sup>2</sup>)
5. 所需辅助空间:O(1)
6. 稳定性:稳定    
<hr />


~~~c++
/*冒泡排序.c*/
#include <stdio.h>
#include <stdlib.h>
void BubbleSort(int *, int );
int main()
{
	int n, num[1000], i;
	
	scanf ("%d", &n);
	for(i = 0; i < n; i++)
	scanf ("%d",num + i);
	
	BubbleSort(num, n);
	for (i = 0;  i < n; i++)
	printf ("%d ", *(num + i));
	return 0;
}
void BubbleSort(int *p, int n)
{
	int i, j, temp;
	for (i = 0; i < n - 1; i++)
	{
		for (j = 0;j < n - 1 - i; j++)
		{
			if (*(p + j) > *(p + j + 1))
			{
			temp = *(p + j);
			*(p + j) = *(p + j + 1);
			*(p + j + 1) = temp;
			}
		}
	}
}
~~~
